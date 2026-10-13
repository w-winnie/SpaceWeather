Set up environment:

cd perceptivespace
conda create --name perceptive python=3.10
conda activate perceptive
pip install numpy matplotlib pandas scikit-learn astropy spicepy xgboost
conda env export > environment.yml
pip freeze > requirements.txt

To recreate from environment.yml file:
conda env create -f environment.yml

## Geomagnetic storm forecast

`notebooks/storm_forecast.ipynb` asks whether Kp three hours ahead will be at least 5 (NOAA G1), using only the solar wind already measured upstream.

The notebook downloads the hourly OMNI2 file from NASA SPDF on first run:

https://spdf.gsfc.nasa.gov/pub/data/omni/low_res_omni/omni2_all_years.dat

The file is cached under `data/` and is not committed. Run the notebook from the repository root. The last cell prints test-set true skill score against persistence and a southward-Bz threshold, plus blocked time-series cross-validation.
