# ab-testing-product-analysis
Python framework for simulating, calculating, and statistically validating A/B test results using Z-tests and Confidence Intervals.

# Product Analysis: A/B Testing & Statistical Validation

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1UYxmPWC8YBvL-VqNRI6W7Ek-bzUhilPl#scrollTo=-cfiJtDvCuvw)
📊 **View the business presentation [here](Product_Analysis_A-B_Testing_&_Statistical_Validation.pdf
)**


## Project Overview
This project demonstrates the end-to-end workflow of an A/B test for a product feature. It simulates an e-commerce scenario where a new UI design (Experimental B) is tested against the current design (Control A) to determine if it drives a higher conversion rate. The project goes beyond simple averages by employing rigorous statistical testing to ensure business decisions are driven by data, not chance.

## The Business Problem
In product development, launching unverified changes can lead to revenue loss. The goal of this analysis is to:
1. Objectively measure the performance of two different designs.
2. Prove mathematically (via a Z-test) whether the observed difference is statistically significant.
3. Provide a clear, actionable business recommendation based on the confidence interval of the improvement.

## Data Simulation
To ensure a controlled environment for the test, a realistic dataset of 2,000 user sessions was procedurally generated using numpy's binomial distribution:
* **Group A (Control):** 1,000 users exposed to the old design (~10% true conversion probability).
* **Group B (Experimental):** 1,000 users exposed to the new design (~13% true conversion probability).

## Statistical Methodology
The core of this project relies on frequentist statistics to validate the results:

1. **Z-Test for Proportions:** Used the `statsmodels` library to calculate the Z-statistic and p-value. This answers the fundamental question: *"Is the observed difference between the groups real, or just statistical noise?"*
2. **Confidence Intervals (CI):** Calculated the point estimate and the 95% Confidence Interval for the difference in proportions ($p_B - p_A$) using the unpooled standard error (SE). This answers the business question: *"If this design is better, exactly how much of a conversion uplift can we expect?"*

## Key Findings & Business Recommendation

* **Conversion Rates:** Group B achieved a visibly higher conversion rate compared to Group A.
* **Statistical Significance:** The calculated p-value fell below the standard alpha threshold of 0.05. This allows us to safely reject the Null Hypothesis and conclude that the new design’s outperformance is **not due to random chance**.
* **Actionable Insight:** The 95% Confidence Interval provides a precise range for the expected uplift. Based on these statistically validated results, the recommendation is to **fully roll out Design B to all users**.

## Tech Stack
* **Python** (Core logic)
* **pandas** (Data manipulation and aggregation)
* **numpy** (Simulating binomial distributions for realistic mock data)
* **statsmodels** (Hypothesis testing and p-value calculation)
* **math** (Manual calculation of Standard Error and Confidence Intervals)
