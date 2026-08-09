Step-by-Step Lab Instructions:
Step 1 — Upload the Case Study Dataset
_______________________________________________________
from google.colab import files
uploaded = files.upload()
Run this cell, then click "Choose Files" and select covid19_malaysia_cases.csv from your computer.
This loads the file into your Colab session so Python can read it.

Step 2 — Import Our Data Analytics Tools
_______________________________________________________
import pandas as pd
import matplotlib.pyplot as plt
We load two toolkits: pandas for working with data tables, and matplotlib for drawing charts. This is
like opening Excel and a charting tool before you start.

Step 3 — Load the Dataset
_______________________________________________________
df = pd.read_csv("covid19_malaysia_cases.csv")
This reads the CSV file into a DataFrame — pandas' name for a data table — stored in a variable
called df, which we reuse for the rest of the lab.

Step 4 — First Look at the Data
_______________________________________________________
df.head()
df.shape
df.info()
head() previews the first 5 rows. shape shows (rows, columns). info() lists every column and its data
type. Always look at your data before doing anything else.

Step 5 — Data Cleaning Basics
_______________________________________________________
df.isnull().sum()
df['date'] = pd.to_datetime(df['date'])
isnull().sum() counts missing values per column. We also convert the date column into a proper
date type so Python treats it as a timeline.

Step 6 — Descriptive Statistics
_______________________________________________________
df.describe()
df['cases_new'].mean()
df['cases_new'].max()
describe() instantly summarizes every numeric column: average, minimum, maximum, and spread.
This is Descriptive Analytics — answering "what happened?"

Step 7 — Visualizing the Trend of Daily Cases
_______________________________________________________
plt.plot(df['date'], df['cases_new'])
plt.title('Daily New COVID-19 Cases in Malaysia')
plt.show()
A line chart reveals the shape of the pandemic — the waves rising and falling — far more clearly
than a table of numbers ever could.

Step 8 — Comparing Cases vs. Deaths
_______________________________________________________
plt.plot(df['date'], df['cases_new'], label='New Cases')
plt.plot(df['date'], df['deaths_new']*100, label='Deaths (x100)')
plt.legend()
plt.show()
Plotting two lines together lets us compare their patterns over time — exactly how health
authorities monitored the severity of each wave.

Step 9 — Vaccination Progress Over Time
_______________________________________________________
plt.plot(df['date'], df['vax_cumul_fully_vaccinated'])
plt.title('Cumulative Fully Vaccinated Population')
plt.show()
A cumulative chart always climbs upward. Its steepness shows the speed of the vaccination rollout
at each point in time.

Step 10 — Finding the Peak: Identifying the Worst Day
_______________________________________________________
peak_day = df.loc[df['cases_new'].idxmax()]
print(peak_day)
idxmax() finds the row with the highest value, pinpointing Malaysia's worst day for new cases — a
first step toward Diagnostic Analytics: asking why.
