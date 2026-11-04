# DATA-ANALYTICS-ABOUT-THE-DATASET
# AIM
To perform data analytics on a given dataset using Python and Pandas, understand the characteristics of the dataset, identify different types of data, examine missing values, and prepare the dataset for further analysis and machine learning.
# THEORY
Data Analytics is the process of collecting, examining, cleaning, and transforming data to discover useful information and support decision-making.

A dataset is a collection of related information arranged in rows and columns. It may contain numerical, categorical, textual, and date-related data.

Python is widely used for data analytics because it provides powerful libraries such as Pandas, NumPy, and Matplotlib.

Pandas is an open-source Python library used for data manipulation and analysis. It provides two important data structures:
1. Series: A one-dimensional labelled data structure.
2. DataFrame: A two-dimensional tabular data structure containing rows and columns.
Data analytics involves the following operations:
- Data Loading: Importing the dataset into Python.
- Data Inspection: Examining the first and last few records.
- Data Understanding: Identifying the number of rows, columns, and data types.
- Statistical Analysis: Calculating mean, median, standard deviation, minimum, and maximum values.
- Missing Value Detection: Identifying empty or null values.
- Duplicate Detection: Finding repeated records in the dataset.
- Data Cleaning: Removing duplicate records and handling missing values.
- Data Visualization: Representing information using charts and graphs.
These operations help improve data quality and prepare the dataset for further analysis and machine learning applications.
3. OBJECTIVES
1. To load a dataset using the Pandas library.
2. To understand the structure and dimensions of the dataset.
3. To identify numerical and categorical data.
4. To perform basic statistical analysis.
5. To detect missing and duplicate values.
6. To clean and preprocess the dataset.
7. To prepare clean data for further machine learning applications.
4. SOFTWARE REQUIREMENTS
S. No.	Software / Tool	Purpose
1	Python	Programming language
2	Jupyter Notebook / Google Colab / VS Code	Code execution
3	Pandas	Data analysis
4	NumPy	Numerical operations
5	Matplotlib	Data visualization

5. ALGORITHM
1. Start the program.
2. Import the required Python libraries.
3. Load the dataset using the Pandas read_csv() function.
4. Display the first five and last five records.
5. Identify the number of rows and columns.
6. Display the column names and data types.
7. Generate descriptive statistical information.
8. Check for missing values in each column.
9. Identify duplicate records.
10. Handle missing values using suitable methods.
11. Remove duplicate records.
12. Save the cleaned dataset as a new CSV file.
13. Display the final dataset information.
14. Stop the program.
6. PYTHON PROGRAM
File name: data_analytics.py

The following program performs dataset loading, inspection, statistical analysis, missing-value detection, duplicate detection, data cleaning, and saving the cleaned dataset.
```
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt

# Step 1: Load the dataset
df = pd.read_csv("dataset.csv")

# Step 2: Display the first five records
print("FIRST FIVE RECORDS:")
print(df.head())

# Step 3: Display the last five records
print("\nLAST FIVE RECORDS:")
print(df.tail())

# Step 4: Display dataset dimensions
print("\nDATASET SHAPE:")
print(df.shape)

# Step 5: Display column names
print("\nCOLUMN NAMES:")
print(df.columns.tolist())

# Step 6: Display dataset information
print("\nDATASET INFORMATION:")
df.info()

# Step 7: Identify data types
print("\nDATA TYPES:")
print(df.dtypes)

# Step 8: Statistical analysis
print("\nSTATISTICAL SUMMARY:")
print(df.describe(include="all"))

# Step 9: Check missing values
print("\nMISSING VALUES:")
print(df.isnull().sum())

# Step 10: Check duplicate records
print("\nDUPLICATE RECORDS:")
print(df.duplicated().sum())

# Step 11: Create a cleaned copy
cleaned_df = df.copy()

# Step 12: Remove duplicate records
cleaned_df = cleaned_df.drop_duplicates()

# Step 13: Handle missing values
for column in cleaned_df.columns:

    if cleaned_df[column].isnull().any():

        if pd.api.types.is_numeric_dtype(cleaned_df[column]):
            cleaned_df[column] = cleaned_df[column].fillna(
                cleaned_df[column].median()
            )

        else:
            mode_values = cleaned_df[column].mode()

            if not mode_values.empty:
                cleaned_df[column] = cleaned_df[column].fillna(
                    mode_values[0]
                )

# Step 14: Display cleaned dataset
print("\nCLEANED DATASET:")
print(cleaned_df.head())

# Step 15: Verify missing values
print("\nMISSING VALUES AFTER CLEANING:")
print(cleaned_df.isnull().sum())

# Step 16: Save cleaned dataset
cleaned_df.to_csv("cleaned_dataset.csv", index=False)

print("\nCleaned dataset saved successfully!")

# Step 17: Visualize missing values before cleaning
missing = df.isnull().sum()

missing = missing[missing > 0]

if not missing.empty:
    missing.plot(kind="bar", title="Missing Values in Dataset")
    plt.xlabel("Columns")
    plt.ylabel("Number of Missing Values")
    plt.tight_layout()
    plt.show()
else:
    print("No missing values found for visualization.")

print("\nDATA ANALYTICS COMPLETED SUCCESSFULLY!")
```
<img width="1389" height="590" alt="image" src="https://github.com/user-attachments/assets/97037287-1f44-4c63-b83c-0664e16bd1d5" />

# RESULT
Thus, data analytics was successfully performed on the given dataset using Python and the Pandas library. The dataset was loaded, inspected, and analysed to identify its structure, data types, statistical characteristics, missing values, and duplicate records. Data cleaning operations were performed, and the processed dataset was saved successfully for further analysis and machine learning applications.
