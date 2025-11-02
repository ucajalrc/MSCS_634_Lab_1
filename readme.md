# **MSCS_634_Lab_1 — Data Visualization, Preprocessing, and Statistical Analysis**

**Name:** *Ajal RC*
**Course:** *MSCS 634 – Big Data and Data Mining*
**Instructor:** *Satish Penmatsa*
**Date:** *11/02/2025*

---

## **1. Purpose of the Lab**

The purpose of this lab was to explore and apply key data analysis techniques using Python and Pandas within a Jupyter Notebook environment. This lab focused on four main objectives:

1. **Data Collection:** Importing and inspecting a real-world health dataset from the CDC Behavioral Risk Factor Surveillance System (BRFSS 2015).
2. **Data Visualization:** Using graphical methods such as histograms, bar charts, and other plots to understand variable distributions and relationships.
3. **Data Preprocessing:** Cleaning, handling missing values, detecting outliers, reducing dataset size, and scaling data for analysis readiness.
4. **Statistical Analysis:** Computing descriptive and inferential statistical measures such as central tendency, dispersion, and correlation to uncover relationships in the data.

This lab demonstrates how effective preprocessing and visualization can improve data quality and support meaningful statistical insights — both critical steps before data mining or machine learning.

---

## **2. Dataset Description**

**Dataset:** *Diabetes 012 Health Indicators (BRFSS 2015)*
**Source:** U.S. Centers for Disease Control and Prevention (CDC), Behavioral Risk Factor Surveillance System (BRFSS) Public Health Survey.
**File:** `diabetes_012_health_indicators_BRFSS2015.csv`

The dataset includes health-related behaviors, chronic health conditions, and preventive service use among adults in the United States. It contains **253,680 records** and **22 columns** representing demographic and health indicators.

**Key Columns:**

* `Diabetes_012`: Target variable (0 = no diabetes, 1 = pre-diabetes, 2 = diabetes)
* `HighBP`, `HighChol`: Cardiovascular risk indicators
* `BMI`: Body Mass Index
* `Smoker`, `PhysActivity`: Lifestyle indicators
* `GenHlth`: Self-rated general health (1 = excellent to 5 = poor)
* `Age`, `Income`: Demographic variables

---

## **3. Folder Structure Overview**

```
📂 MSCS_634_Lab_1
 ┣ 📂 Screenshots
 ┃ ┣ 📂 Data Collection Step 1
 ┃ ┃ ┗ diabetes_data_description.png
 ┃ ┣ 📂 Data Visualization Step 2
 ┃ ┃ ┣ average_BMI_by_diabetes_status.png
 ┃ ┃ ┣ BMI_distribution_data_visualization.png
 ┃ ┃ ┗ self_reported_general_health_by_diabetes_status.png
 ┃ ┣ 📂 Data Preprocessing Step 3
 ┃ ┃ ┣ dataset_before_handling_missing_values_3.1.png
 ┃ ┃ ┣ dataset_after_handling_missing_values_3.1.png
 ┃ ┃ ┣ IQR_calculation_with_outliers_3.2.png
 ┃ ┃ ┣ dataset_before_and_after_reduction_3.3.png
 ┃ ┃ ┣ dataset_before_and_after_scaling_3.4.png
 ┃ ┃ ┗ discretization_example_nice_to_have.png
 ┃ ┗ 📂 Statistical Analysis Step 4
 ┃ ┃ ┣ overview_of_data_4.1.png
 ┃ ┃ ┣ central_tendency_calculation_4.2.png
 ┃ ┃ ┣ dispersion_calculation_4.3.png
 ┃ ┃ ┗ correlation_analysis_4.4.png
 ┣ diabetes_012_health_indicators_BRFSS2015.csv
 ┗ lab1.ipynb
```

---

## **4. Summary of Steps and Key Insights**

### **Step 1: Data Collection**

The dataset was loaded using Pandas’ `read_csv()` function and verified with `.head()` to display the first five rows.
**Insight:** The dataset was structured and required no format conversion. Each column represented a numeric health indicator suitable for statistical computation.

---

### **Step 2: Data Visualization**

**Visualizations Created:**

1. **Histogram of BMI Distribution:** Revealed that most participants had BMI values between 25 and 35, indicating a predominantly overweight population sample.
2. **Bar Chart of Average BMI by Diabetes Status:** Showed that average BMI was significantly higher among participants diagnosed with diabetes.
3. **Bar Chart of Average General Health (GenHlth) by Diabetes Status:** Demonstrated that individuals with diabetes rated their general health worse than those without the condition.

**Insight:** The visualizations confirmed known health patterns — higher BMI and poorer self-reported health correlate with diabetes risk.

---

### **Step 3: Data Preprocessing**

**Techniques Applied:**

1. **Handling Missing Values:**

   * Checked for missing values using `.isnull().sum()`.
   * Although the dataset had no NaNs, the process was demonstrated using `fillna(mean)` for numeric columns.
   * Screenshots show dataset state before and after imputation.

2. **Outlier Detection (IQR Method):**

   * Calculated Q1, Q3, and IQR for BMI.
   * Identified and removed BMI values beyond 1.5 × IQR bounds.
   * Reduced data shape after filtering indicates cleaner, less skewed data.

3. **Data Reduction:**

   * Randomly sampled 70% of records for efficiency using `.sample(frac=0.7)`.
   * Dropped less relevant columns (e.g., `Fruits`) to simplify analysis.

4. **Data Scaling:**

   * Applied **Min–Max normalization** to rescale numerical columns between 0 and 1.
   * Ensured features like BMI and Age contribute equally to correlation and distance-based analyses.

5. **Discretization (Optional):**

   * Created a `BMI_Category` column categorizing continuous BMI into labeled health groups (Normal, Overweight, Obese).

**Insight:**
Data preprocessing improved consistency, reduced noise, and prepared the dataset for robust statistical or machine learning applications.

---

### **Step 4: Statistical Analysis**

1. **General Overview (`.info()` and `.describe()`):**

   * Confirmed dataset contained 70% of original rows with no missing values and numeric consistency across all columns.

2. **Central Tendency:**

   * Computed **mean, median, and mode** for each variable.
   * The average BMI (~0.56 after scaling) and median health ratings (~0.5) represent a balanced distribution post-normalization.

3. **Dispersion:**

   * Calculated **range, variance, standard deviation, and IQR** to evaluate variability across health indicators.
   * Features like BMI and GenHlth displayed moderate dispersion, indicating diversity in population health characteristics.

4. **Correlation Analysis:**

   * Generated a correlation matrix using `.corr()`.
   * Found strong positive correlation between `HighBP`, `HighChol`, and `Diabetes_012`, confirming biological interdependence.
   * Negative correlation between `PhysActivity` and `Diabetes_012` suggested that physical activity is protective.

**Insight:**
The statistical summaries quantitatively confirmed patterns observed in Step 2’s visualizations — overweight, poor general health, and high blood pressure contribute to higher diabetes likelihood.

---

## **5. Challenges Faced**

* Interpreting categorical codes (0, 1, 2) required reviewing BRFSS data documentation.
* Managing outliers in a very large dataset demanded careful computation to prevent excessive data loss.
* Ensuring scaling did not distort interpretability while maintaining comparability across variables.
* Organizing multiple screenshots systematically for each lab requirement.

---

## **6. Key Takeaways**

* Effective **data cleaning and preprocessing** are essential for trustworthy results in data mining.
* Visualizations serve as the first checkpoint to identify relationships and data issues.
* **Statistical analysis** quantifies those patterns, building the foundation for clustering, classification, and predictive modeling.
* This lab reinforces the importance of reproducibility and transparency through Jupyter notebooks and GitHub documentation.

---

## **7. Tools and Libraries Used**

* **Python 3.10+**
* **Pandas** – data loading, cleaning, preprocessing, and statistics
* **Matplotlib** – visualizations and plots
* **NumPy** – numeric operations and array manipulation
* **Jupyter Notebook** – interactive environment for analysis and documentation

---

## Some console outputs and table results shown in the screenshots were truncated or partially hidden due to limited screen space. When the notebook is executed directly in Jupyter, full outputs are visible in scrollable cells. The screenshots provided capture the key portions necessary to verify successful run for each step.