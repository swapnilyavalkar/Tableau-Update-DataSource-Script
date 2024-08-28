---

# 🗄️ Tableau Server Data Connection Update Script

This Python script automates the process of updating specific data connections in Tableau Server, particularly targeting Oracle connections. It fetches data from a PostgreSQL database and updates the connection information on Tableau Server accordingly.

## 🚀 Features

- **Database Integration**: Connects to a PostgreSQL database to retrieve relevant data.
- **Data Connection Update**: Automatically updates Oracle database connections on Tableau Server.
- **Logging**: Provides detailed output during execution for easy troubleshooting.
- **Excel Reporting**: Exports both the original data and updated connection details to Excel files.

## 🛠️ Prerequisites

Ensure the following components are set up before running the script:

- **Python 3.8+** installed
- **Required Python Libraries**: Install using `pip install -r requirements.txt`
- **PostgreSQL**: The script connects to a PostgreSQL database to fetch data.
- **Tableau Server Client (TSC)**: The script interacts with Tableau Server using the `tableauserverclient` library.
- **Configuration File**: Ensure your `config.py` file is properly set up with PostgreSQL connection details.

## 📋 Script Overview

This script operates through a sequence of steps:

### 1. **Initialize Connection to PostgreSQL Database**
   - Establishes a connection to the PostgreSQL database using credentials from the `config.py` file.
   - Executes an SQL query to retrieve data relevant to Tableau data sources.

### 2. **Export Initial Data**
   - Converts the retrieved data into a Pandas DataFrame and exports it to an Excel file named `data-all-ds.xlsx`.

### 3. **Authenticate with Tableau Server**
   - Uses the Tableau Server Client (TSC) to authenticate with Tableau Server using credentials provided in the script.

### 4. **Process Each Site**
   - Iterates through all Tableau Server sites, matching them with the data retrieved from PostgreSQL.
   - Switches the Tableau Server context to the appropriate site for each iteration.

### 5. **Update Data Connections**
   - Locates the relevant data sources and updates Oracle connection details based on specific conditions.
   - Logs and stores updated connection details in a DataFrame.

### 6. **Export Processed Data**
   - Exports the DataFrame with updated connection details to an Excel file named `df_processed_ds.xlsx`.

## 📂 Directory Structure

```bash
├── sql-query.sql              # SQL query file used to fetch data from PostgreSQL
├── data-all-ds.xlsx           # Exported file with initial data from PostgreSQL
├── df_processed_ds.xlsx       # Exported file with updated connection details
├── config.py                  # Configuration file with database connection details
└── script.py                  # Main Python script
```

## ⚙️ Configuration

### **config.py**
Make sure your `config.py` contains the correct connection parameters for your PostgreSQL database:

```python
def configpg():
    return {
        'dbname': 'your_db_name',
        'user': 'your_db_user',
        'password': 'your_db_password',
        'host': 'your_db_host',
        'port': 'your_db_port'
    }
```

### **Script Variables**

- **SERVER_URL**: URL of your Tableau Server.
- **TS_USER_NAME**: Tableau Server username.
- **TS_PASSWORD**: Tableau Server password.
- **SITE_NAME**: Name of the Tableau site (if applicable).

## 🚨 Error Handling

The script includes a basic exception handling mechanism that prints any errors that occur during execution. Errors are logged with a message to help identify the point of failure.

## 🧑‍💻 How to Run

1. **Clone the Repository**: Clone this repository to your local machine.
2. **Install Dependencies**: Run `pip install -r requirements.txt` to install necessary packages.
3. **Update Configuration**: Ensure that your `config.py` and script variables are correctly set.
4. **Run the Script**: Execute the script using `python script.py`.
5. **Review Outputs**: Check the generated Excel files (`data-all-ds.xlsx` and `df_processed_ds.xlsx`) for initial and updated connection details.

## 🛡️ License

This script is licensed under the MIT License. See the `LICENSE` file for more information.

---

Feel free to adjust any section to better fit your needs or style!