# cricket-performance-eda
A Python-based Exploratory Data Analysis (EDA) tool that processes local cricket match statistics to visualize player consistency and strike rates.
import pandas as pd
import matplotlib.pyplot as plt

def analyze_match_data():
    print("--- Cricket Performance Analyzer Initialized ---")
    
    # 1. Creating a mock dataset (In a real project, this would be a .csv file)
    data = {
        'Match_Week': ['Week 1', 'Week 2', 'Week 3', 'Week 4', 'Week 5'],
        'Runs_Scored': [45, 12, 67, 34, 89],
        'Balls_Faced': [30, 15, 40, 28, 50]
    }
    
    # Load data into a Pandas DataFrame
    df = pd.DataFrame(data)
    
    # 2. Feature Engineering: Calculate Strike Rate
    df['Strike_Rate'] = (df['Runs_Scored'] / df['Balls_Faced']) * 100
    
    print("\nProcessed Data:")
    print(df.to_string(index=False))
    
    # 3. Data Visualization
    plt.figure(figsize=(8, 5))
    plt.plot(df['Match_Week'], df['Runs_Scored'], marker='o', color='b', label='Runs Scored')
    plt.bar(df['Match_Week'], df['Strike_Rate'], alpha=0.3, color='orange', label='Strike Rate')
    
    plt.title('Weekly Cricket Performance Analysis')
    plt.xlabel('Match Timeline')
    plt.ylabel('Metrics')
    plt.legend()
    plt.grid(True)
    
    # Save the plot as an image file
    plt.savefig('performance_plot.png')
    print("\nSuccess! Visualization saved as 'performance_plot.png'")

if __name__ == "__main__":
    analyze_match_data()
