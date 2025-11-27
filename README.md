**Customer Lifetime Value (CLV) Prediction Project Report**

**1. Introduction & Abstract**
**1.1 Introduction**
The objective of this project was to build a predictive model to estimate the Customer Lifetime Value (CLV) of existing clients. Accurately predicting CLV allows the marketing and sales departments to optimize customer acquisition costs, prioritize retention efforts, and segment the customer base for personalized strategies.
**1.2 Abstract**
This study utilized the IBM Watson Marketing dataset, applying feature engineering and an XGBoost Regressor to predict CLV. The model was trained on historical customer attributes and achieved strong performance after applying a log transformation to correct the right-skewed nature of the target variable. Final segmentation placed customers into High-, Medium-, and Low-Value tiers, delivering actionable insights for strategic decision-making.

**2. Tools Used**
•	Python: Core language for data manipulation, modeling, and analysis.
•	Pandas & NumPy: Data cleaning, preprocessing, and numerical transformations.
•	Scikit-learn (Sklearn): Data splitting, scaling, and validation metrics.
•	XGBoost: Primary regression algorithm used.
•	Matplotlib & Seaborn: Visualization of model insights including feature importance.

**3. Steps Involved in Building the Project**
•	Data Preparation: Removal of identifiers and irrelevant time-series data; one-hot encoding of categorical features; standardization of numerical features.
•	Target Transformation: Log-transform of skewed CLV values using ln(1 + x) to stabilize model training.
•	Model Training: XGBoost Regressor trained on the processed feature matrix.
•	Validation: Performance evaluated on the original currency scale by reversing the log transform.
•	Segmentation: Predicted CLV used to segment customers into Top 25%, Middle 50%, and Bottom 25% groups.

**4. Model Performance and Key Insights**
**4.1 Model Accuracy**
The model was evaluated on the held-out test set, with predictions converted back to the original dollar values.
Metric	Result	Interpretation
Mean Absolute Error (MAE)	$1,458.94	On average, the predicted LTV is off by this dollar amount.
Root Mean Squared Error (RMSE)	$4,170.68	Penalizes larger errors and is approximately 2.8x higher than the MAE, indicating the presence of significant outliers.
Interpretation of Results:
The MAE shows that the prediction for an individual customer will be off by roughly $1,459. This establishes the expected accuracy for forecasting and budgeting. However, the significantly higher RMSE (more than 2.8x the MAE) indicates the presence of occasional large prediction deviations (outliers), which is typical for skewed financial data such as CLV.
**4.2 Feature Importance Analysis**
The feature importance chart reveals the strongest drivers of CLV.
**Top 3 Predictors:**
•	num__Number_of_Policies
•	num__Monthly_Premium_Auto
•	cat__Response_No
 


**Key Insight:**
The model places far more emphasis on product-related metrics than demographic factors. The number of policies a customer holds and their monthly auto premium are the strongest indicators of future value. The top predictor, num__Number_of_Policies, shows that product depth is the primary driver of CLV. This suggests that initial product depth and upselling success are the most reliable predictors of long-term value.

**5. Conclusion: Strategic Suggestions**
The predictive model successfully segmented the customer base as follows:
LTV Segment	Count	Profit Strategy
High-Value (Top 25%)	2284	Retention: Focus on premium, proactive customer service and exclusive offers. Since these customers typically hold a higher number of policies, retention efforts should prioritize multi-policy clients to prevent significant revenue loss.
Medium-Value	4566	Growth: This group represents the strongest upsell/cross-sell opportunity. Strategies should aim to increase monthly premium auto and policy count to move these customers into the High-Value tier.
Low-Value (Bottom 25%)	2284	Efficiency: Improve acquisition targeting to reduce low-value inflow. For current customers, use automated, low-cost marketing channels to sustain engagement.


