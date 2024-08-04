# HMO-Data-Analysis
________________________________________________________________________________________________________________________________________
Overview

This project is part of the IST 687 Introduction to Data Science course at Syracuse University under Prof. Jeffrey Saltz. The goal of this project is to analyze Health Maintenance Organization (HMO) data to identify trends and build predictive models. The dataset is provided by the course professor and is available on AWS cloud.
________________________________________________________________________________________________________________________________________
Contributors

Omkar Sabnis
Omkar Dabholkar
Diya Shah
Shweta Khopde
________________________________________________________________________________________________________________________________________
License

BSD 2-Clause License

Copyright (c) 2024, Omkar Sabnis, Omkar Dabholkar, Diya Shah, Shweta Khopde

Redistribution and use in source and binary forms, with or without
modification, are permitted provided that the following conditions are met:

1. Redistributions of source code must retain the above copyright notice, this
   list of conditions and the following disclaimer.

2. Redistributions in binary form must reproduce the above copyright notice,
   this list of conditions and the following disclaimer in the documentation
   and/or other materials provided with the distribution.

THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS "AS IS"
AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE
IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE ARE
DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT HOLDER OR CONTRIBUTORS BE LIABLE
FOR ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL
DAMAGES (INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR
SERVICES; LOSS OF USE, DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER
CAUSED AND ON ANY THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY,
OR TORT (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE
OF THIS SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.
________________________________________________________________________________________________________________________________________
Project Structure

The repository contains the following files and directories:

IST687_Final_Project.Rmd: The main R Markdown file containing all the code and analysis.

README.md: This readme file.

LICENSE: This is a BSD 2-Clause License Document.
________________________________________________________________________________________________________________________________________
Data

The dataset used in this project is an HMO dataset available on AWS cloud. It includes various attributes related to individuals' health metrics and costs. ("https://intro-datascience.s3.us-east-2.amazonaws.com/HMO_data.csv")
________________________________________________________________________________________________________________________________________
Steps and Analysis

1. Library Installation and Loading
We start by installing and loading the necessary R packages. These include:

dplyr and tidyverse for data manipulation.
ggplot2 for data visualization.
caret for machine learning.
kernlab for Support Vector Machines.
rpart and rpart.plot for decision trees.
shiny for interactive applications.
imputeTS for handling missing values.
rio for data import/export.
arules and arulesViz for association rule mining.

2. Data Loading
We load the dataset from AWS using the read_csv function. The data is stored in a variable called data.

3. Data Exploration
We explore the dataset using functions like:

head(data) to view the first few rows.
str(data) to understand the structure of the dataset.
summary(data) to get summary statistics.

4. Data Cleaning
Handling Missing Values

We check for missing values using colSums(is.na(data)) and anyNA(data).
We interpolate missing values in the bmi and hypertension columns using na_interpolation.
Removing Outliers

We identify outliers in the cost variable using a boxplot.
We calculate the Interquartile Range (IQR) and remove outliers beyond 1.5 times the IQR.
Creating New Variables

We create a binary variable expensive to indicate if the cost is greater than 5000.
We define another variable exp for costs greater than 4000 and convert it to a factor.

5. Feature Engineering
We create a new dataframe HMO with the important variables for analysis:

age, bmi, smoker, yearly_physical, exercise, hypertension, and exp.

6. Data Partitioning
We split the data into training (85%) and testing (15%) sets using the createDataPartition function from the caret package.

Support Vector Machine (SVM)

We build an SVM model using the ksvm function from the kernlab package.
We predict the test set and evaluate the model using a confusion matrix.
Decision Tree

We build a decision tree model using the rpart function.
We predict the test set and evaluate the model using a confusion matrix.
Linear Model

We convert exp to numeric and build a linear model using the lm function.
We summarize the linear model to interpret the results.

7. Data Visualization
We create various visualizations to explore the data:

Histograms for variables like age, bmi, cost, etc.
Boxplots for bmi, age, hypertension, and cost.
Scatter plots showing relationships between variables like bmi and cost, age and cost.
Maps showing cost distribution and average age across states using ggplot2 and map_data.

8. Interactive Application
We use the shiny package to create an interactive web application to visualize the data.
________________________________________________________________________________________________________________________________________
How to Run

To run the project, follow these steps:

Ensure you have all the required packages installed.
Load the IST687_Final_Project.Rmd file in RStudio.
Knit the R Markdown file to produce the HTML or Word output.
To run the Shiny app, ensure the shiny package is installed and run the app from the R Markdown file.
