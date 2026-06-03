# FestRide Survey Data Analysis

This repository contains the analysis of survey data from FestRide, aiming to provide key insights for the leadership team through visual dashboards and analytical reports.

## Project Task
Analyze the survey data from "/content/FestRide Survey - FestRide Survey.csv" to create a visual dashboard/analytical report with at least 5 charts summarizing key insights for FestRide's leadership team. Include a short summary (3-5 key insights) for management.

## Setup and Data Loading

First, we load the necessary libraries and the survey data into a pandas DataFrame.

```python
import pandas as pd

df = pd.read_csv('/content/FestRide Survey - FestRide Survey.csv')
```

Displaying the first few rows to verify successful data loading:

```python
df.head()
```

## Data Exploration

We examine the structure of the dataset by checking column names and data types.

```python
print("Column Names:")
print(df.columns)
print("\nData Types:")
print(df.dtypes)
```

## Data Cleaning and Preparation

We check for missing values and inspect unique values in categorical columns to identify any inconsistencies.

```python
print("Missing values per column:")
print(df.isnull().sum())

categorical_cols = ['Country', 'City', 'Gender', 'Age Group', 'Preferred Ride-Hailing App', 'Model (Service Type)', 'Reason for Booking', 'Why Preferred (Key Factor)', 'Preferred Payment Option', 'Last Booking Timeframe']

print("\nUnique values in categorical columns:")
for col in categorical_cols:
    print(f"\n--- {col} ---")
    print(df[col].unique())
```

## Data Analysis and Visualization

We create several visualizations to highlight key insights from the survey data.

### 1. Distribution of Respondents by Country

```python
import matplotlib.pyplot as plt
import seaborn as sns

plt.figure(figsize=(10, 6))
sns.countplot(data=df, x='Country', palette='viridis')
plt.title('Distribution of Respondents by Country')
plt.xlabel('Country')
plt.ylabel('Number of Respondents')
plt.xticks(rotation=45, ha='right')
plt.tight_layout()
plt.show()
```

### 2. Distribution of Respondents by City

```python
plt.figure(figsize=(12, 6))
sns.countplot(data=df, x='City', palette='viridis')
plt.title('Distribution of Respondents by City')
plt.xlabel('City')
plt.ylabel('Number of Respondents')
plt.xticks(rotation=45, ha='right')
plt.tight_layout()
plt.show()
```

### 3. Distribution of Preferred Ride-Hailing App

```python
plt.figure(figsize=(12, 6))
sns.countplot(data=df, x='Preferred Ride-Hailing App', palette='viridis')
plt.title('Distribution of Preferred Ride-Hailing App')
plt.xlabel('Preferred Ride-Hailing App')
plt.ylabel('Number of Respondents')
plt.xticks(rotation=45, ha='right')
plt.tight_layout()
plt.show()
```

### 4. Comparison of Service Types by Country

```python
plt.figure(figsize=(12, 7))
sns.countplot(data=df, x='Country', hue='Model (Service Type)', palette='viridis')
plt.title('Comparison of Service Types by Country')
plt.xlabel('Country')
plt.ylabel('Number of Respondents')
plt.xticks(rotation=45, ha='right')
plt.legend(title='Service Type')
plt.tight_layout()
plt.show()
```

### 5. Correlation between Reason for Booking and Preferred Payment Option

```python
plt.figure(figsize=(12, 8))
ct = pd.crosstab(df['Reason for Booking'], df['Preferred Payment Option'])
sns.heatmap(ct, annot=True, fmt='d', cmap='viridis')
plt.title('Correlation between Reason for Booking and Preferred Payment Option')
plt.xlabel('Preferred Payment Option')
plt.ylabel('Reason for Booking')
plt.tight_layout()
plt.show()
```

### 6. Last Booking Timeframe across Age Groups

```python
plt.figure(figsize=(12, 7))
sns.countplot(data=df, x='Age Group', hue='Last Booking Timeframe', palette='viridis')
plt.title('Last Booking Timeframe across Age Groups')
plt.xlabel('Age Group')
plt.ylabel('Number of Respondents')
plt.legend(title='Last Booking Timeframe')
plt.tight_layout()
plt.show()
```

## Key Insights for FestRide Management

Based on the analysis, here are the key insights:

1.  **Geographic Focus**: The majority of respondents are concentrated in Nigeria (Lagos), South Africa (Johannesburg), Kenya (Nairobi), Egypt (Cairo), and Ghana (Accra). FestRide should prioritize strategies for growth and market penetration in these key cities and countries.

2.  **Competitive Landscape**: While FestRide is a preferred app for a significant portion of respondents, there are other strong competitors in the market. Understanding the "Why Preferred (Key Factor)" for both FestRide and its competitors is crucial for refining FestRide's value proposition and marketing efforts.

3.  **Service Type Preferences**: The popularity of "Ride" services is consistent across all surveyed countries. "Delivery" services show varying levels of adoption by country, suggesting opportunities for targeted marketing or service adjustments in specific regions.

4.  **Payment Option Trends**: Mobile Money and Card/Wallet in-App are the most preferred payment options across various booking reasons, particularly for commuting and business meetings. Cash is still significant for errands and shopping. This suggests the importance of maintaining diverse payment options while potentially promoting digital payments for certain use cases.

5.  **Booking Frequency by Age**: The 'Within the last week' timeframe for booking is strong across all age groups, indicating a relatively high frequency of recent usage. The 25-34 and 35-44 age groups show particularly high recent activity. This information can help tailor marketing campaigns and loyalty programs to different age segments.

## Summary: Data Analysis Key Findings

*   The dataset contains 11 columns, mostly of object data type, suitable for categorical analysis.
*   No missing values were found in the dataset.
*   Nigeria (Lagos), South Africa (Johannesburg), Kenya (Nairobi), Egypt (Cairo), and Ghana (Accra) are key geographic markets.
*   "Ride" services are consistently popular across all surveyed countries.
*   Mobile Money and Card/Wallet in-App are the most preferred payment methods, especially for commuting and business meetings.
*   Cash remains a significant payment method for errands and shopping.
*   Recent booking activity ('Within the last week') is strong across all age groups, with particular strength in the 25-34 and 35-44 age brackets.

## Insights or Next Steps

*   FestRide should focus on strengthening its presence and tailoring strategies for the key cities and countries identified.
*   Further analysis into the factors driving preference for FestRide and its competitors can help refine FestRide's value proposition and marketing.
*   Maintaining diverse payment options while promoting digital payments for specific use cases aligns with user preferences.
*   Targeted marketing campaigns and loyalty programs could be developed based on booking frequency trends across different age groups.
