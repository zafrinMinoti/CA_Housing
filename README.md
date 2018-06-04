download the dataset using the code below.
Explore the data.
Make new features if needed. Bin data where needed. Convert to categorical when needed. Investigate the range of Y. 
Task: build the best regressor you can to fit the house values based on the features provided. Investigate alternative loss functions to see if that improves your model results. Note: The best result I've seen quoted (using techniques available in scikit learn) is R2 = 0.84. 
import os
import tarfile
from six.moves import urllib
import pandas as pd
DOWNLOAD_ROOT = "https://raw.githubusercontent.com/ageron/handson-ml/master/"
HOUSING_PATH = os.path.join("datasets", "housing")
HOUSING_URL = DOWNLOAD_ROOT + "datasets/housing/housing.tgz"
def fetch_housing_data(housing_url=HOUSING_URL, housing_path=HOUSING_PATH):
    if not os.path.isdir(housing_path):
        os.makedirs(housing_path)
    tgz_path = os.path.join(housing_path, "housing.tgz")
    urllib.request.urlretrieve(housing_url, tgz_path)
    housing_tgz = tarfile.open(tgz_path)
    housing_tgz.extractall(path=housing_path)
    housing_tgz.close()
    
def load_housing_data(housing_path=HOUSING_PATH):
    csv_path = os.path.join(housing_path, "housing.csv")
    return pd.read_csv(csv_path)
fetch_housing_data()
housing = load_housing_data()
housing.head()

