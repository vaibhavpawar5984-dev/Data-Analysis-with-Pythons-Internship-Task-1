


from google.colab import files
uploaded = files.upload()
     
Upload widget is only available when the cell has been executed in the current browser session. Please rerun this cell to enable.
Saving student-mat.csv.csv to student-mat.csv.csv

# Step 1: Import Libraries
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

# Step 2: Load Dataset
df = pd.read_csv("student-mat.csv", sep=';')

# Step 3: Explore Data
print("Dataset Shape:", df.shape)
print("\nData Types:\n", df.dtypes)

# Step 4: Check Missing Values
print("\nMissing Values:\n", df.isnull().sum())

# Step 5: Remove Duplicates
df.drop_duplicates(inplace=True)
print("\nShape after removing duplicates:", df.shape)

# Step 6: Analysis

# Average final grade (G3)
avg_grade = df['G3'].mean()
print("\nAverage Final Grade (G3):", avg_grade)

# Students scored above 15
above_15 = df[df['G3'] > 15].shape[0]
print("Students scored above 15:", above_15)

# Study time vs performance correlation
correlation = df['studytime'].corr(df['G3'])
print("Correlation between study time and G3:", correlation)

# Gender wise performance
gender_avg = df.groupby('sex')['G3'].mean()
print("\nAverage Score by Gender:\n", gender_avg)

# Step 7: Visualizations

# Histogram of grades
plt.figure()
plt.hist(df['G3'], bins=10)
plt.xlabel("Final Grade (G3)")
plt.ylabel("Number of Students")
plt.title("Histogram of Final Grades")
plt.show()

# Scatter plot: study time vs grades
plt.figure()
plt.scatter(df['studytime'], df['G3'])
plt.xlabel("Study Time")
plt.ylabel("Final Grade (G3)")
plt.title("Study Time vs Final Grade")
plt.show()

# Bar chart: Male vs Female average score
plt.figure()
gender_avg.plot(kind='bar')
plt.xlabel("Gender")
plt.ylabel("Average Final Grade")
plt.title("Average Score by Gender")
plt.show()
     
Dataset Shape: (395, 33)

Data Types:
 school        object
sex           object
age            int64
address       object
famsize       object
Pstatus       object
Medu           int64
Fedu           int64
Mjob          object
Fjob          object
reason        object
guardian      object
traveltime     int64
studytime      int64
failures       int64
schoolsup     object
famsup        object
paid          object
activities    object
nursery       object
higher        object
internet      object
romantic      object
famrel         int64
freetime       int64
goout          int64
Dalc           int64
Walc           int64
health         int64
absences       int64
G1             int64
G2             int64
G3             int64
dtype: object

Missing Values:
 school        0
sex           0
age           0
address       0
famsize       0
Pstatus       0
Medu          0
Fedu          0
Mjob          0
Fjob          0
reason        0
guardian      0
traveltime    0
studytime     0
failures      0
schoolsup     0
famsup        0
paid          0
activities    0
nursery       0
higher        0
internet      0
romantic      0
famrel        0
freetime      0
goout         0
Dalc          0
Walc          0
health        0
absences      0
G1            0
G2            0
G3            0
dtype: int64

Shape after removing duplicates: (395, 33)

Average Final Grade (G3): 10.415189873417722
Students scored above 15: 40
Correlation between study time and G3: 0.09781968965319626

Average Score by Gender:
 sex
F     9.966346
M    10.914439
Name: G3, dtype: float64



Introduction :
In this task, we analyze the Student Performance dataset using Python. The goal is to understand student grades and factors affecting performance.

Dataset Loading :
The dataset is loaded using pandas. It contains academic and personal details of students along with their final grades.

Data Cleaning :
We checked for missing values and removed duplicate records to ensure clean and accurate analysis.

Data Analysis :
We calculated the average final grade, identified high-performing students, analyzed the relation between study time and performance, and compared male and female students.

Visualization :
Graphs were created to visually understand grade distribution, study habits, and gender-wise performance.

Conclusion :
From the analysis, study time shows a positive relationship with performance. Gender-wise comparison shows a slight difference in average scores. Visualizations help in better understanding the data trends.
