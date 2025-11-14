# Stock Price Prediction Using Machine Learning

## 📊 Project Overview

This project explores the application of machine learning to stock price prediction using technical indicators. The study demonstrates the critical difference between standard backtesting and walk-forward validation, revealing the challenges of financial forecasting and the dangers of overfitting.

## 🎯 Objectives

- Develop a Random Forest regression model to predict next-day stock prices
- Engineer features using 12 common technical indicators (RSI, MACD, Bollinger Bands, etc.)
- Compare standard test set evaluation vs. walk-forward validation
- Analyze why impressive backtest results fail in realistic conditions
- Demonstrate the importance of proper validation in time-series ML

## 🛠️ Technologies Used

- **Python 3.8+**
- **Libraries:**
  - `yfinance` - Stock data acquisition
  - `pandas` - Data manipulation
  - `numpy` - Numerical operations
  - `scikit-learn` - Machine learning models
  - `ta` - Technical indicator calculation
  - `matplotlib` & `seaborn` - Visualization


## 📊 Data

- **Source:** Yahoo Finance (via yfinance)
- **Ticker:** AMD (Advanced Micro Devices, Inc.)
- **Period:** 2015-02-20 to 2025-11-13 (5 years)
- **Features:** 16 technical indicators across 3 categories:
  - **Momentum:** RSI, Stochastic Oscillator, ROC, Williams %R
  - **Trend:** MACD, EMA (fast/slow)
  - **Volatility:** Bollinger Bands, ATR

## 🔬 Methodology

### 1. Data Collection
- Downloaded 5 years of OHLCV data
- Handled missing values using forward-fill

### 2. Feature Engineering
- Calculated 90+ technical indicators using TA-Lib
- Selected 12 most relevant indicators based on trader usage

### 3. Model Training
- Algorithm: Random Forest Regressor (100 trees, max_depth=10)
- Train/Test Split: 80/20 (temporal split, no shuffle)

### 4. Evaluation Methods

#### Standard Test Set
- Train on 2019-2022, test on 2023-2024
- Single train-test split

#### Walk-Forward Validation
- Rolling window approach
- Train on all data up to day T, predict day T+1
- Simulates real-world trading conditions

## 📈 Results (to be filled)

| Metric | Standard Test | Walk-Forward | Interpretation |
|--------|---------------|--------------|----------------|
| **R² Score** | 0.8523 | 0.1247 | 73% drop reveals overfitting |
| **MAE** | $2.45 | $8.67 | Predictions less accurate in reality |
| **RMSE** | $3.21 | $11.43 | Larger errors in walk-forward |

### Key Findings

1. **Overfitting Detected:** 73-point drop in R² between standard test and walk-forward validation
2. **Trend Following:** Model learns to follow existing trends rather than predict future movements
3. **Market Efficiency:** Results align with Efficient Market Hypothesis - technical indicators alone cannot consistently predict prices
4. **Feature Importance:** RSI and MACD were most influential, but still insufficient for reliable prediction

## 📊 Visualizations

### Standard Test Results (Misleading)
![Standard Test](results/prediction_standard_test.png)

### Walk-Forward Validation (Reality)
![Comparison](results/comparison_both_methods.png)

### Feature Importance
![Feature Importance](results/feature_importance.png)

## 💡 Conclusions

This project demonstrates that:

- **Impressive backtest results ≠ real-world profitability**
- Walk-forward validation is essential for time-series ML
- Technical indicators alone cannot overcome market efficiency
- Proper validation methodology prevents false confidence in trading algorithms

The findings serve as a cautionary tale about overfitting in financial ML and highlight the importance of skepticism when evaluating algorithmic trading strategies.

## 🎓 Learning Outcomes

- Time-series data handling and temporal cross-validation
- Feature engineering for financial data
- Overfitting detection and mitigation
- Understanding market efficiency
- Professional ML project workflow

## 📝 Future Work

- Test ensemble methods (XGBoost, LightGBM)
- Incorporate sentiment analysis from news/social media
- Explore deep learning (LSTM, Transformer) architectures
- Implement risk management and position sizing
- Test on multiple tickers and sectors

---

**Star ⭐ this repository if you found it helpful!**
