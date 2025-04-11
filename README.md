# Library Insights

This repository contains code for training a model that predicts whether a bookstore customer will return a borrowed book on time.

The analysis is based on four input tables:

1. `checkouts`  
2. `customers`  
3. `books`  
4. `libraries`  

---

## Notebooks

The repository includes the following key notebooks:

1. **`01_checkouts_table.ipynb`** – Exploratory data analysis (EDA), preprocessing, and cleaning of the `checkouts` table. Saves the cleaned version to the `data_preprocessed` directory.  
2. **`02_books.ipynb`** – EDA and preprocessing of the `books` table. Outputs a preprocessed version to the `data_preprocessed` directory.  
3. **`03_customers.ipynb`** – EDA and preprocessing of the `customers` table. Saves the processed table to the `data_preprocessed` directory.  
4. **`04_modeling.ipynb`** – Trains and evaluates the predictive model using data from the previous notebooks. Final conclusions are provided at the end of this notebook.  
5. **`api_data_download.ipynb`** – Downloads additional data from external sources:  
   - Uses OpenAI’s API to infer missing customer genders  
   - Uses Google Maps API to retrieve full addresses and calculate distances between customers and libraries  
   - Saves data to the `new_data` directory and an enriched `libraries` table to the `data_preprocessed` directory  
   - Uses meteostat library to retrieve weather data

---

## How to Run This Code

1. **Install dependencies** using Poetry:
   ```bash
   poetry install --no-root
   ```

2. **Set up API keys** in a `.env` file:

   - For OpenAI:
     ```
     OPEN_API_KEY=your_key_here
     ```

   - For Google Maps:
     - Install the `googlemaps` Python package
     - Create a Google Cloud account, enable billing, and activate the Maps API
     - Add to `.env`:
       ```
       GOOGLE_KEY=your_google_maps_key_here
       ```

3. **Create required directories**:
   - `data_preprocessed` – to store all preprocessed tables  
   - `new_data` – to store all newly created or downloaded data (e.g. from APIs)

---

## Execution Order

1. `api_data_download.ipynb`  
2. `01_checkouts_table.ipynb`, `02_books.ipynb`, `03_customers.ipynb`  
3. `04_modeling.ipynb`  

---

## Input Data

The original input files must be placed in a directory named `data`, with the following filenames:

- `books.csv`  
- `checkouts.csv`  
- `customers.csv`  
- `libraries.csv`
