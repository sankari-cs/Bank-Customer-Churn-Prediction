# Bank Customer Churn Prediction using Logistic Regression

## Project Overview

This project develops a **Logistic Regression model** to predict whether a bank customer is likely to churn.

Customer churn is an important concern for banks because retaining existing customers is generally more cost-effective than acquiring new customers. A churn prediction model can help identify customers who may be at higher risk of leaving and support customer-retention strategies.

---

## Objectives

* Perform detailed Exploratory Data Analysis (EDA)
* Understand the distribution of customer churn
* Identify relevant demographic, financial, and banking-related features
* Handle categorical variables using encoding
* Analyze multicollinearity using Variance Inflation Factor (VIF)
* Build a Logistic Regression model
* Evaluate the model using classification metrics
* Analyze the confusion matrix and ROC curve
* Interpret Logistic Regression coefficients and odds ratios
* Identify important factors associated with customer churn

---

## Dataset

The dataset contains information about bank customers, their characteristics, account details, and churn status.

### Important Variables

| Variable           | Description                                             |
| ------------------ | ------------------------------------------------------- |
| `customer_id`      | Unique customer identifier                              |
| `credit_score`     | Customer credit score                                   |
| `country`          | Customer's country                                      |
| `gender`           | Customer's gender                                       |
| `age`              | Customer's age                                          |
| `tenure`           | Number of years the customer has been with the bank     |
| `balance`          | Customer account balance                                |
| `products_number`  | Number of bank products used                            |
| `credit_card`      | Whether the customer has a credit card                  |
| `active_member`    | Whether the customer is an active bank member           |
| `estimated_salary` | Estimated customer salary                               |
| `churn`            | Target variable indicating whether the customer churned |

### Target Variable

```text
churn
0 → Customer stayed
1 → Customer churned
```

---

## Exploratory Data Analysis

The following analyses were performed:

* Dataset shape and structure
* Data types
* Missing-value analysis
* Duplicate-value analysis
* Unique-value analysis
* Descriptive statistics
* Churn distribution
* Age analysis
* Balance analysis
* Credit-score analysis
* Correlation analysis
* Multicollinearity analysis

### EDA Visualizations

The project includes visualizations for understanding customer characteristics and their relationship with churn.

---

## Data Preprocessing

The dataset was checked for missing values and duplicate records.

### Missing Values

No missing values were found in the dataset.

### Duplicate Records

No duplicate rows were identified.

### Categorical Variables

The categorical variables `country` and `gender` were converted into numerical representations using one-hot encoding.

The binary variables such as:

* `credit_card`
* `active_member`
* `churn`

were already represented numerically.

---

## Multicollinearity Analysis

Variance Inflation Factor (VIF) was calculated to identify multicollinearity among the predictor variables.

The final VIF analysis produced the following results:

| Feature          |       VIF |
| ---------------- | --------: |
| credit_score     | 21.236445 |
| age              | 12.334128 |
| products_number  |  7.826417 |
| estimated_salary |  3.887186 |
| tenure           |  3.872755 |
| credit_card      |  3.289605 |
| balance          |  3.182267 |
| gender_Male      |  2.168988 |
| active_member    |  2.075966 |
| country_Germany  |  1.787170 |
| country_Spain    |  1.486247 |

The analysis indicates that `credit_score` and `age` have relatively high VIF values, while several other variables show acceptable levels of multicollinearity.

---

## Machine Learning Model

### Logistic Regression

Logistic Regression was selected because the target variable is binary:

```text
0 → Stayed
1 → Churned
```

The model estimates the probability that a customer belongs to the churn class.

---

## Model Evaluation

The Logistic Regression model was evaluated using:

* Accuracy
* Precision
* Recall
* F1-Score
* ROC-AUC
* Confusion Matrix
* ROC Curve

### Results

| Metric    |                  Value |
| --------- | ---------------------: |
| Accuracy  | 0.8080                 |               
| Precision |  0.5891                |
| Recall    | 0.1867                 |
| F1-Score  |  0.2836                |
| ROC-AUC   | 0.7748                 |

Replace the values above with the actual output from the notebook.

---

## Confusion Matrix

The confusion matrix was used to examine the individual classification outcomes.

The four possible outcomes are:

* **True Negative (TN):** Customer stayed and was correctly predicted to stay.
* **False Positive (FP):** Customer stayed but was incorrectly predicted to churn.
* **False Negative (FN):** Customer churned but was incorrectly predicted to stay.
* **True Positive (TP):** Customer churned and was correctly predicted to churn.

The confusion matrix provides more detailed information than accuracy alone.

---

## ROC Curve

The ROC curve evaluates the ability of the Logistic Regression model to distinguish between customers who churn and customers who remain with the bank.

The **ROC-AUC** value summarizes the model's discriminatory ability.

An AUC closer to 1 indicates stronger classification performance, while an AUC near 0.5 indicates performance close to random classification.

---

## Feature Importance

The Logistic Regression coefficients were analyzed to understand the relationship between predictor variables and customer churn.

A **positive coefficient** indicates an association with increased log-odds of churn.

A **negative coefficient** indicates an association with decreased log-odds of churn.

The coefficient magnitudes were used to compare the relative contribution of standardized numerical features.

---

## Odds Ratio Analysis

Odds ratios were calculated using:

```text
Odds Ratio = exp(Coefficient)
```

Interpretation:

| Odds Ratio | Interpretation             |
| ---------- | -------------------------- |
| > 1        | Increased odds of churn    |
| < 1        | Decreased odds of churn    |
| ≈ 1        | Small effect on churn odds |

This analysis provides an interpretable way to understand how individual variables are associated with customer churn.

---

## Key Insights

1. Customer churn is not evenly distributed across the dataset.
2. Customer age can be an important factor associated with churn.
3. Credit score provides additional financial information for churn prediction.
4. Account balance can contribute to understanding customer behavior.
5. The number of products used by a customer provides information about the customer's relationship with the bank.
6. Active membership can indicate customer engagement.
7. Country and gender were encoded so they could be incorporated into the Logistic Regression model.
8. Precision and recall provide more detailed information than accuracy alone.
9. ROC-AUC provides an overall measure of the model's ability to distinguish churned and retained customers.
10. Logistic Regression coefficients and odds ratios make the model relatively interpretable.
11. VIF analysis identified potential multicollinearity among some predictor variables.
12. The model can potentially help banks identify customers at higher risk of leaving and support targeted retention strategies.

---

## Technologies Used

* Python
* Pandas
* NumPy
* Matplotlib
* Seaborn
* Scikit-learn
* Statsmodels
* Google Colab
* Jupyter Notebook

## 15. Multicollinearity Analysis

Variance Inflation Factor (VIF) was calculated to identify potential multicollinearity among the predictor variables.

The general interpretation of VIF values is:

|  VIF | Interpretation              |
| ---: | --------------------------- |
|    1 | No multicollinearity        |
|  1–5 | Generally acceptable        |
| 5–10 | High multicollinearity      |
|  >10 | Very high multicollinearity |

The VIF results are shown below:

| Feature          |       VIF |
| ---------------- | --------: |
| credit_score     | 21.236445 |
| age              | 12.334128 |
| products_number  |  7.826417 |
| estimated_salary |  3.887186 |
| tenure           |  3.872755 |
| credit_card      |  3.289605 |
| balance          |  3.182267 |
| gender_Male      |  2.168988 |
| active_member    |  2.075966 |
| country_Germany  |  1.787170 |
| country_Spain    |  1.486247 |

The results indicate high multicollinearity for `credit_score` and `age`, while `products_number` also shows a relatively high VIF. Most of the remaining variables have VIF values below 5 and therefore show relatively acceptable levels of multicollinearity.

## 16. Results and Discussion

The Logistic Regression model was developed to predict customer churn using demographic, financial, and banking-related variables.

The final model achieved the following performance:

| Metric    |      Value |
| --------- | ---------: |
| Accuracy  | **0.8080** |
| Precision | **0.5891** |
| Recall    | **0.1867** |
| F1-Score  | **0.2836** |
| ROC-AUC   | **0.7748** |

The accuracy of **80.80%** indicates that the model correctly classified approximately 81% of the test observations.

The precision of **58.91%** indicates that among the customers predicted as churners, approximately 59% actually churned.

The recall of **18.67%** indicates that the model identified approximately 19% of the customers who actually churned. This relatively low recall indicates that the model misses a substantial number of potential churners.

The F1-score of **0.2836** reflects the balance between precision and recall and is affected by the relatively low recall.

The ROC-AUC of **0.7748** indicates that the model has a reasonable ability to distinguish between customers who churn and customers who remain with the bank.

The confusion matrix provides additional information about correctly and incorrectly classified customers, while the ROC curve provides an overall view of the model's classification capability.

Feature coefficient and odds-ratio analysis were used to understand the relationship between predictor variables and customer churn. Positive coefficients indicate increased estimated log-odds of churn, while negative coefficients indicate decreased estimated log-odds of churn.

## 17. Key Insights

The analysis provides the following major insights:

1. Customer churn is not evenly distributed across the dataset, making class distribution important when interpreting model performance.
2. Customer age can be an important factor associated with churn behavior.
3. Credit score provides additional financial information that can be considered when predicting churn.
4. Account balance can contribute to understanding differences in customer behavior.
5. The number of products used by a customer provides information about the customer's relationship with the bank.
6. Active membership can provide an indication of customer engagement.
7. Country and gender were converted into numerical variables using one-hot encoding.
8. Accuracy alone does not provide a complete picture of churn prediction performance.
9. The low recall of **18.67%** indicates that the model does not identify a large proportion of actual churners.
10. The ROC-AUC of **0.7748** indicates reasonable discrimination between churned and retained customers.
11. Logistic Regression coefficients and odds ratios provide an interpretable way to examine the relationship between features and churn.
12. VIF analysis identified substantial multicollinearity for `credit_score` and `age`, which should be considered when interpreting individual coefficients.
13. The model can potentially support banks in identifying customers at risk of leaving and developing targeted customer-retention strategies.

## 18. Conclusion

A Logistic Regression model was developed to predict customer churn for ABC Bank. The dataset contained no missing values or duplicate records, and exploratory data analysis was performed to investigate relationships between customer characteristics and churn.

Categorical variables were converted into numerical form using one-hot encoding, while the customer identifier was removed because it does not provide meaningful predictive information.

The Logistic Regression model was trained using an 80:20 train-test split and evaluated using Accuracy, Precision, Recall, F1-Score, Confusion Matrix, and ROC-AUC.

The model achieved an accuracy of **80.80%** and an ROC-AUC of **0.7748**, indicating reasonable overall classification capability. However, the recall of **18.67%** shows that the model failed to identify many actual churners. Therefore, further model improvement, threshold tuning, class-balancing techniques, or alternative classification algorithms could be considered if the primary objective is to identify as many potential churners as possible.

Overall, the project demonstrates how Logistic Regression and exploratory data analysis can be used to identify patterns associated with customer churn and support data-driven customer-retention strategies.


## Project Structure

```text
Bank-Customer-Churn-Prediction/
│
├── Bank_Customer_Churn_Prediction.ipynb
├── README.md
├── requirements.txt
│
└── plots/
    ├── churn_distribution.png
    ├── age_vs_churn.png
    ├── balance_vs_churn.png
    ├── credit_score_vs_churn.png
    ├── correlation_heatmap.png
    ├── confusion_matrix.png
    ├── roc_curve.png
    └── feature_importance.png

## How to Run

1. Clone or download the repository.
2. Open `Bank_Customer_Churn_Prediction.ipynb` using Google Colab or Jupyter Notebook.
3. Download the original dataset from Kaggle.
4. Place the dataset in the required location.
5. Install the dependencies listed in `requirements.txt`.
6. Run the notebook cells sequentially.
7. Review the EDA, model evaluation, confusion matrix, ROC curve, and feature analysis.

---
