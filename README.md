# 📈 Marketing Analytics: Facebook vs. AdWords A/B Test

![Python](https://img.shields.io/badge/Python-3.9-blue)
![Library](https://img.shields.io/badge/Library-Pandas%20%7C%20Seaborn%20%7C%20Scipy-orange)
![Status](https://img.shields.io/badge/Status-Complete-green)

## 📌 Executive Summary
**Objective:** Compare the performance of two parallel marketing campaigns (Facebook Ads vs. Google AdWords) run throughout 2019 to optimize the marketing budget for the upcoming year.
**Method:** Time-Series Analysis & Paired T-Tests on 365 days of campaign data.
**Key Findings:**
* **Facebook** was the clear winner in both effectiveness and efficiency.
* **Conversion Rate:** Facebook (27.1%) > AdWords (10.2%).
* **Cost Per Acquisition (CPA):** Facebook ($8.07) < AdWords ($24.71).
**Recommendation:** Reallocate budget from AdWords to Facebook to maximize ROI, while auditing AdWords targeting to improve quality.

---

## 📂 Data Overview
The dataset contains 365 rows (daily data for 2019) with performance metrics for both platforms.

| Feature | Definition |
| :--- | :--- |
| **Date** | Daily observation (Jan 1 - Dec 31, 2019) |
| **Ad Views** | Total impressions/views for the day |
| **Ad Clicks** | Total user clicks on the ad |
| **Ad Conversions** | Total purchases/leads generated |
| **Cost per Ad** | Total daily spend ($) |
| **CTR (Click-Through Rate)** | % of views that resulted in a click |
| **Conversion Rate** | % of clicks that resulted in a sale |
| **CPC (Cost Per Click)** | Average cost paid for one click |

---

## 🛠️ Methodology

### 1. Data Cleaning & Engineering
* **Cleaning:** Removed special characters (`$`, `%`) from numerical columns and converted them to floats.
* **Feature Engineering:**
    * `CPA` (Cost Per Acquisition): Calculated as $\frac{\text{Total Cost}}{\text{Total Conversions}}$.
    * `Day_of_Week`: Extracted to analyze weekly performance cycles.
* **Data Integrity:** Verified no missing values or days with 0 conversions (Infinite CPA checks).

### 2. Exploratory Data Analysis (EDA)
I visualized the distribution of clicks and costs to identify stability and trends.

<img width="1389" height="490" alt="image" src="https://github.com/user-attachments/assets/ed1cc263-46a1-4c6a-8c1b-0f971903f42e" />

*Observation: Facebook's conversion rate distribution (Blue) is significantly shifted to the right compared to AdWords (Green), indicating consistently higher lead quality.*

---

## 🧪 Hypothesis Testing
Since the data is time-dependent (same market conditions affect both platforms daily), I used a **Paired T-Test** to check for statistical significance.

### Test 1: Effectiveness (Conversion Rate)
* $H_0$: $\mu_{FB} - \mu_{AW} = 0$
* $H_1$: $\mu_{FB} - \mu_{AW} \neq 0$
* **Result:** P-Value $\approx 0.00$ (T-Stat: 65.98)
* **Conclusion:** **REJECT** Null Hypothesis. Facebook converts significantly better.

### Test 2: Efficiency (Cost Per Acquisition)
* $H_0$: $\mu_{FB} - \mu_{AW} = 0$
* $H_1$: $\mu_{FB} - \mu_{AW} \neq 0$
* **Result:** P-Value $\approx 0.00$ (T-Stat: -29.14)
* **Conclusion:** **REJECT** Null Hypothesis. Facebook is significantly cheaper.

---

## 📊 Results Visualization

The final analysis highlights the magnitude of the difference between the two platforms.

<img width="1589" height="1189" alt="image" src="https://github.com/user-attachments/assets/b6c5cf4d-c292-4601-9d3d-1359903a82c9" />

| Metric | Facebook (Avg) | AdWords (Avg) | Difference |
| :--- | :--- | :--- | :--- |
| **Conversion Rate** | **27.15%** | 10.18% | +16.97% (Better) |
| **Cost Per Acquisition** | **$8.07** | $24.71 | -$16.64 (Cheaper) |

---

## 💡 Business Recommendations
Based on the statistical evidence, the following actions are recommended:

1.  **Aggressive Budget Shift:** Move 30-50% of the AdWords budget to Facebook. Facebook is acquiring customers at **1/3rd the cost** of AdWords.
2.  **Strategic Review of AdWords:** AdWords users have a high Click-Through Rate (CTR) but low Conversion Rate. This suggests "Window Shopping" behavior.
    * *Action:* Refine negative keywords to filter out low-intent searchers.
    * *Action:* Improve landing page relevance for Search traffic.
3.  **Weekend Optimization:** Data shows consistent performance across the week; ensure budget caps do not throttle traffic on high-performing weekends.

---

## 💻 How to Run This Project
1.  Clone the repository:
    ```bash
    git clone [https://github.com/YourUsername/marketing-ab-test.git](https://github.com/YourUsername/marketing-ab-test.git)
    ```
2.  Install dependencies:
    ```bash
    pip install pandas numpy seaborn scipy matplotlib
    ```
3.  Run the Jupyter Notebook:
    ```bash
    jupyter notebook notebooks/Marketing_Campaign_Analysis.ipynb
    ```
