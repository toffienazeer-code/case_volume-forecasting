# Customer Case Volume Forecasting

Forecasts daily customer-support case volume 7 days ahead, using
pandas and scikit-learn, so a support team can plan staffing.

## Results (last 180 days, held-out test set)
| Model | MAE (cases/day) | MAPE |
|---|---|---|
| Same day last week (baseline) | 19.7 | 5.1% |
| Gradient boosting (ratio target) | 21.8 | 5.6% |

## Key findings
- Trees can't extrapolate growth, so the model predicts cases / recent level.
- Slow-drifting features (e.g. email share) leak time and hurt generalization.
- The seasonal baseline is hard to beat on this regular series.

## Setup
pip install -r requirements.txt
Place `customer_cases.csv` in `data/`, then open `notebooks/case_volume_forecast.ipynb`.

## Data
Columns: case_id, date_time, customer_id, channel, reason.
