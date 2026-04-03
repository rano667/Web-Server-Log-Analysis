# Web Server Log Analysis - Python

## Overview
This project analyzes the Calgary HTTP dataset, which contains approximately one year of web server logs from the University of Calgary. The goal of this assessment is to process raw log data, extract meaningful insights, and demonstrate efficient data handling and analysis using Python.

---

## Dataset Information
- **Dataset Name:** Calgary HTTP Dataset  
- **Format:** ASCII text (Apache Common Log Format)  
- **Size:** ~52 MB (uncompressed)  
- **Source:** http://ita.ee.lbl.gov/html/contrib/Calgary-HTTP.html  

Each log entry represents a single HTTP request and includes:
- Host (request origin)
- Timestamp
- HTTP method and requested resource
- Status code
- Response size (bytes)

---

## Approach

### 1. Data Loading
- The dataset is compressed in `.gz` format and is processed using Python’s `gzip` module.
- A streaming approach is used to read the file line-by-line, ensuring memory efficiency.

### 2. Data Parsing and Cleaning
- Regular expressions are used to parse each log entry.
- Timestamps are converted into `datetime` objects for time-based analysis.
- File extensions are extracted from requested filenames.
- Invalid or malformed entries are skipped.
- Missing values (e.g., `-` in bytes field) are handled appropriately.

### 3. Data Processing
Efficient data structures such as `Counter`, `defaultdict`, and `set` are used to compute metrics in a single pass through the dataset.

---

## Analysis Tasks

The following key metrics were computed:

1. Total number of log records  
2. Number of unique hosts  
3. Date-wise count of unique filenames  
4. Number of 404 (Not Found) responses  
5. Top 15 filenames causing 404 errors  
6. Top 15 file extensions causing 404 errors  
7. Total bandwidth transferred per day (July 1995)  
8. Hourly request distribution  
9. Top 10 most requested filenames  
10. HTTP response code distribution  

---

## Key Insights

- The dataset contains over 700,000 requests, indicating substantial server activity.
- Traffic increases significantly over time, showing growing usage of the server.
- Peak traffic occurs during working hours (13:00–16:00), while early mornings show the lowest activity.
- Most requests are successful (HTTP 200), indicating stable server performance.
- A significant number of 304 responses suggests effective browser caching.
- Approximately 3% of requests result in 404 errors, with `index.html` being the most frequently missing file.
- Traffic is heavily concentrated on a small number of resources, particularly the homepage and image files.
- Bandwidth usage shows noticeable spikes on certain days, indicating periods of high activity or large file transfers.

---

## Visualizations

The analysis includes the following visualizations:
- Hourly request distribution
- HTTP status code distribution
- Top requested files
- Daily bandwidth usage (July 1995)
- Trend of unique files requested over time


---

## Tools and Technologies
- Python
- gzip (file handling)
- re (regular expressions)
- datetime
- collections (Counter, defaultdict)
- matplotlib (visualization)

---

## How to Run

1. Download the dataset and place it in the project directory.
2. Open `analysis.ipynb` in Jupyter Notebook.
3. Run all cells sequentially to reproduce the analysis.

---

## Conclusion

This project demonstrates efficient processing of large-scale log data using Python. By combining structured parsing, optimized data aggregation, and clear visualization, the analysis provides meaningful insights into server behavior, performance, and usage patterns.

---

## Project Structure
