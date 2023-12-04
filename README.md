# csp_554_project
Snowflake for Machine Learning and AI(Using Snowpark)


1) Set up the Snowflake environment
Run the following SQL commands in a SQL worksheet to create the warehouse, database and schema.

SE ROLE ACCOUNTADMIN;
CREATE OR REPLACE WAREHOUSE ML_HOL_WH; --by default, this creates an XS Standard Warehouse
CREATE OR REPLACE DATABASE ML_HOL_DB;
CREATE OR REPLACE SCHEMA ML_HOL_SCHEMA;
CREATE OR REPLACE STAGE ML_HOL_ASSETS; --to store model assets

-- create csv format
CREATE FILE FORMAT IF NOT EXISTS ML_HOL_DB.ML_HOL_SCHEMA.CSVFORMAT 
    SKIP_HEADER = 1 
    TYPE = 'CSV';

-- create external stage with the csv format to stage the diamonds dataset
CREATE STAGE IF NOT EXISTS ML_HOL_DB.ML_HOL_SCHEMA.DIAMONDS_ASSETS 
    FILE_FORMAT = ML_HOL_DB.ML_HOL_SCHEMA.CSVFORMAT 
    URL = 's3://sfquickstarts/intro-to-machine-learning-with-snowpark-ml-for-python/diamonds.csv';
    -- https://sfquickstarts.s3.us-west-1.amazonaws.com/intro-to-machine-learning-with-snowpark-ml-for-python/diamonds.csv

LS @DIAMONDS_ASSETS;



2)  Set up the Python environment

Create the conda environment.
conda env create -f conda_env.yml

Activate the conda environment.
conda activate snowpark-ml-hol

Optionally start notebook server:
$ jupyter notebook &> /tmp/notebook.log &


3) Please update the connection.json file according to your snowflake credentials and account identifiers i have used mine for this

4) Please follow the prefix number for the .ipynb files as they are in order.

5) Conclusion
The integration of Snowpark ML offers a streamlined approach to leverage machine learning insights within Snowflake, promoting a cohesive and efficient data analytics environment.
