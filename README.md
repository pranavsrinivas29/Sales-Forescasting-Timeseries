🏪 Store Sales - Time Series Forecasting

Kaggle Competition Project

This repository contains my end-to-end solution to the Store Sales - Time Series Forecasting competition on Kaggle. The goal of the competition is to predict daily unit sales for thousands of items sold at different stores, leveraging both historical sales data and associated time-based, store-related, oil price, and holiday features.

Link to competition: https://www.kaggle.com/competitions/store-sales-time-series-forecasting/overview

| Dataset               | Shape          | Description                                   |
| --------------------- | -------------- | --------------------------------------------- |
| `train.csv`           | (3,000,888, 6) | Historical daily sales with item & store info |
| `test.csv`            | (28,512, 5)    | Target rows for prediction                    |
| `stores.csv`          | (54, 5)        | Store location + type + cluster metadata      |
| `oil.csv`             | (1,218, 2)     | Daily oil price values                        |
| `holidays_events.csv` | (350, 6)       | Local, regional, and national holiday signals |

| Feature Group    | Examples                                                                       |
| ---------------- | ------------------------------------------------------------------------------ |
| Time-Based       | `day_of_week`, `day_of_month`, `month`, `year`, `is_month_end`, `is_month_mid` |
| Holiday Features | Binary holiday indicator + holiday type                                        |
| Store Metadata   | `store_type`                                                                   |
| External Factors | `dcoilwtico` (Oil price)                                                       |

| Model                             | Status | RMSLE (Validation) | Notes                                      |
| --------------------------------- | ------ | ------------------ | ------------------------------------------ |
| **RandomForestRegressor**         | ✅      | **1.18**          |Tuned depth, leaf size, features           |
| **HistGradientBoostingRegressor** | ✅      | **1.71**          | Stable, but less competitive               |
| **Neural Network (Keras)**        | ✅      | **~1.62**         | Needs sequence-based input for improvement |

🚀 Results & Insights

- Feature engineering played a bigger role than model complexity.
- Oil price & holiday signals improved performance noticeably.
- Neural networks require windowed time-series inputs to outperform tree models.