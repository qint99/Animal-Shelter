# Animal-Shelter
capture metrics like total surrender applications and adoption rates, and it will allow for trend analysis to inform operational strategies.
pip install pandas matplotlib
import pandas as pd
import matplotlib.pyplot as plt

# Sample data: You might load this from a CSV file or database in practice
data = {
    'Date': pd.date_range(start='2022-01-01', periods=12, freq='M'),
    'Total Surrenders': [20, 25, 22, 30, 35, 40, 38, 36, 33, 30, 28, 45],
    'Total Adoptions': [15, 18, 20, 25, 30, 35, 33, 31, 34, 38, 40, 50]
}

# Creating a DataFrame
df = pd.DataFrame(data)

# Calculating monthly adoption rates as a percentage of surrenders
df['Adoption Rate'] = (df['Total Adoptions'] / df['Total Surrenders']) * 100

# Plotting the data
plt.figure(figsize=(10, 5))
plt.plot(df['Date'], df['Total Surrenders'], label='Total Surrenders', marker='o')
plt.plot(df['Date'], df['Total Adoptions'], label='Total Adoptions', marker='o')
plt.plot(df['Date'], df['Adoption Rate'], label='Adoption Rate %', linestyle='--', color='red')
plt.title('Animal Shelter Metrics Tracking')
plt.xlabel('Date')
plt.ylabel('Count')
plt.legend()
plt.grid(True)
plt.show()

# Saving the DataFrame to a new Excel file
# Ensure you have 'openpyxl' installed to use with Excel
df.to_excel('animal_shelter_data.xlsx', index=False)

print("Data saved to 'animal_shelter_data.xlsx'. Trend analysis complete.")
