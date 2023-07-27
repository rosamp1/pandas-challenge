# pandas-challenge
Background
You are the new Chief Data Scientist for your city's school district. In this capacity, you'll be helping the school board and mayor make strategic decisions regarding future school budgets and priorities.
As a first task, you've been asked to analyze the district-wide standardized test results. You'll be given access to every student's math and reading scores, as well as various information on the schools they attend. Your task is to aggregate the data to showcase obvious trends in school performance.
District Summary
Perform the necessary calculations and then create a high-level snapshot of the district's key metrics in a DataFrame.
Include the following:
Total number of unique schools
Total students
Total budget
Average math score
Average reading score
% passing math (the percentage of students who passed math)
% passing reading (the percentage of students who passed reading)
% overall passing (the percentage of students who passed math AND reading)
School Summary
Perform the necessary calculations and then create a DataFrame that summarizes key metrics about each school.
Include the following:
School name
School type
Total students
Total school budget
Per student budget
Average math score
Average reading score
% passing math (the percentage of students who passed math)
% passing reading (the percentage of students who passed reading)
% overall passing (the percentage of students who passed math AND reading)
Highest-Performing Schools (by % Overall Passing)
Sort the schools by % Overall Passing in descending order and display the top 5 rows.
Save the results in a DataFrame called "top_schools".
Lowest-Performing Schools (by % Overall Passing)
Sort the schools by % Overall Passing in ascending order and display the top 5 rows.
Save the results in a DataFrame called "bottom_schools".
Math Scores by Grade
Perform the necessary calculations to create a DataFrame that lists the average math score for students of each grade level (9th, 10th, 11th, 12th) at each school.
Reading Scores by Grade
Create a DataFrame that lists the average reading score for students of each grade level (9th, 10th, 11th, 12th) at each school.
Scores by School Spending
Create a table that breaks down school performance based on average spending ranges (per student).
Use the code provided below to create four bins with reasonable cutoff values to group school spending.
spending_bins = [0, 585, 630, 645, 680]
labels = ["<$585", "$585-630", "$630-645", "$645-680"]
Use pd.cut to categorize spending based on the bins.
Use the following code to then calculate mean scores per spending range.
spending_math_scores = school_spending_df.groupby(["Spending Ranges (Per Student)"])["Average Math Score"].mean()
spending_reading_scores = school_spending_df.groupby(["Spending Ranges (Per Student)"])["Average Reading Score"].mean()
spending_passing_math = school_spending_df.groupby(["Spending Ranges (Per Student)"])["% Passing Math"].mean()
spending_passing_reading = school_spending_df.groupby(["Spending Ranges (Per Student)"])["% Passing Reading"].mean()
overall_passing_spending = school_spending_df.groupby(["Spending Ranges (Per Student)"])["% Overall Passing"].mean()
Use the scores above to create a DataFrame called spending_summary.
Include the following metrics in the table:
Average math score
Average reading score
% passing math (the percentage of students who passed math)
% passing reading (the percentage of students who passed reading)
% overall passing (the percentage of students who passed math AND reading)
Scores by School Size
Use the following code to bin the per_school_summary.
size_bins = [0, 1000, 2000, 5000]
labels = ["Small (<1000)", "Medium (1000-2000)", "Large (2000-5000)"]
Use pd.cut on the "Total Students" column of the per_school_summary DataFrame.
Create a DataFrame called size_summary that breaks down school performance based on school size (small, medium, or large).
Scores by School Type
Use the per_school_summary DataFrame from the previous step to create a new DataFrame called type_summary.
This new DataFrame should show school performance based on the "School Type".





**Resources:**
Assistance on pd.cut from Chat GPT:

To categorize spending based on the specified bins using pd.cut, you can do the following:
pythonCopy code

import pandas as pd

# Assuming you have already established the bins and labels
spending_bins = [0, 585, 630, 645, 680]
labels = ["<$585", "$585-630", "$630-645", "$645-680"]

# Create a copy of the school summary DataFrame since it has the "Per Student Budget"
school_spending_df = per_school_summary.copy()

# Use pd.cut to categorize spending based on the bins.
school_spending_df["Spending Ranges (Per Student)"] = pd.cut(school_spending_df["Per Student Budget"], bins=spending_bins, labels=labels)

# Display the updated DataFrame
print(school_spending_df)
In this example, we assumed you have a DataFrame called per_school_summary that contains the "Per Student Budget" column, and you have already established the spending_bins and labels lists. We then create a copy of per_school_summary called school_spending_df and use pd.cut to categorize the "Per Student Budget" based on the spending_bins. The results will be stored in a new column called "Spending Ranges (Per Student)" in the DataFrame school_spending_df.

Although most of code in this challenge is from class session, below was used as a guiding post:
https://github.com/bdthai81/pandas-challenge/blob/master/PyCitySchools/PyCitySchools_starter.ipynb
