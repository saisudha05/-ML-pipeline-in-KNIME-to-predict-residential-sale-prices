# ML-pipeline-in-KNIME-to-predict-residential-sale-prices
A KNIME-based machine learning pipeline that predicts residential house sale prices in King County, Washington, comparing Linear Regression against Random Forest Regression.

**#📌Overview**
This project implements a complete regression workflow — from raw data to model evaluation — using the KNIME Analytics Platform. It covers data ingestion, exploratory data analysis, preprocessing, feature engineering, model training, and evaluation across two regression algorithms.

Dataset: King County House Sales (Kaggle) — 21,613 residential property sales (2014–2015), 21 original features.

**#🎯 Results**
Metric	Linear Regression	Random Forest	Improvement
R²	          0.668	       0.861	      +28.9%
MAE	          0.342	       0.194	      −43.2%
RMSE	        0.536	       0.347	      −35.3%
Random Forest substantially outperforms Linear Regression across every metric, driven by its ability to capture non-linear relationships between features like house age, grade, and location that a linear model structurally can’t represent.

**#🔧 Pipeline**
The workflow consists of 16 nodes across six phases:

Data Ingestion — CSV Reader + Column Filter (21 → 19 features, dropped id and date)
Exploratory Data Analysis — Histogram + Statistics nodes; revealed a heavily right-skewed price distribution (skewness = 4.02)
Preprocessing — Z-score normalization across all features; missing-value checkpoint
Feature Engineering — derived house_age (from yr_built) and total_sqft (merged sqft_above + sqft_basement to reduce multicollinearity)
Train/Test Split — 80/20 random partition (17,290 train / 4,323 test rows)
Model Training & Evaluation — Linear Regression and Random Forest (100 trees), each scored with R², MAE, RMSE, and Mean Signed Difference

**#🛠️ Tools**
KNIME Analytics Platform — visual workflow / pipeline execution
Nodes used: CSV Reader, Column Filter, Histogram, Statistics, Normalizer, Missing Value, Math Formula, Partitioning, Linear Regression Learner/Predictor, Random Forest Learner/Predictor, Numeric Scorer, Scatter Plot
**#🚀 Future Improvements**
Apply a log transformation to the price target to directly address the right-skew
Add interaction features between location and property size
Test gradient boosting (XGBoost / LightGBM) against Random Forest
Implement cross-validation for more robust evaluation
**#📄 Full Report**
See report.pdf for the complete write-up, including detailed node configurations, coefficient tables, and feature importance rankings.

Author
Saisudha Baskaran Master’s student in Data Science
