# ETL Server Access Log Processing DAG

This repository contains the code for an Apache Airflow Directed Acyclic Graph (DAG) named "ETL_Server_Access_Log_Processing." The purpose of this DAG is to perform Extract, Transform, and Load (ETL) operations on a web server access log file.

## Overview

This DAG consists of four tasks:

1. **Download (task_id='download')**: This task downloads the web server access log file from a specified URL using the `wget` command.

2. **Extract (task_id='extract')**: In this task, the relevant fields from the downloaded log file are extracted using the `cut` command. The extracted data is then saved to a new file named "extracted.txt."

3. **Transform (task_id='transform')**: The extracted data is transformed by converting all lowercase letters to uppercase using the `tr` command. The transformed data is saved to a new file named "capitalized.txt."

4. **Load (task_id='load')**: The final task compresses the transformed data file ("capitalized.txt") into a ZIP file named "log.zip" using the `zip` command.

## DAG Configuration

The DAG is configured with the following parameters:

- **DAG Name**: ETL_Server_Access_Log_Processing
- **Description**: My first DAG
- **Start Date**: The DAG is set to start immediately (`days_ago(0)`).
- **Email Notification**: Email notifications are configured for the owner ('Victor Olushola') in case of task failure.
- **Schedule Interval**: The DAG is scheduled to run daily (`timedelta(days=1)`).

## Task Dependencies

The tasks are arranged in a linear pipeline, where each task depends on the successful completion of the previous task:

download >> extract >> transform >> load

This ensures that the tasks are executed in the correct order, and the entire ETL process is completed seamlessly.

## Instructions for Use

1. Install Apache Airflow.
2. Copy the DAG file (ETL_Server_Access_Log_Processing.py) to the dags directory in your Airflow installation.
3. Start the Airflow web server and scheduler.
4. Access the Airflow web UI in your browser (usually http://localhost:8080).
5. Navigate to the "DAGs" tab in the UI and enable the "ETL_Server_Access_Log_Processing" DAG.
6. Trigger the DAG manually. 



## Author

- **Author**: Victor Olushola

customize and extend this DAG according to your specific requirements.
