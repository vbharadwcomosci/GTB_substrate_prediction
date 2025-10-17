![Image](https://github.com/user-attachments/assets/6348e0b8-d708-473b-aec0-0b1a65ff1ee0)


Model Overview:

GTBPredict works with a starting csv file, consisting of all the proteins included in both the training and testing sets. It then uses this data to grab the relevant sequences from Uniprot and the AlphaFold2 structures. It then parses the AlphaFold2 structures to find the Rossmann domains and will only use this segment of the sequence and structure. Any samples not containing these domains are excluded. It also filters the GTBs into training and testing sets by ensuring no test sequence is more than 75% similar to a training sequence, as well as ensuring about 1/5 of each substrate samples are placed into the test set. It then aligns the training sequences into an MSA and then converts this MSA into features like charge, accessible surface area, polarity, as well as features from the structure, such as secondary structure and solvent accessible surface area. Next, it trains the K Nearest Neighbor, Random Forest, Support Vector, and Gaussian Naive Bayes models with this data, while selecting the best feature subsets and hyperparameters. The test set samples are indivdually aligned to the training MSA, and used to check the peformance of the model. For more detail, see the notebook, where every function is explained.

For notebook and dataset installation:

Clone dataset:

```
git clone https://github.com/vbharadwcomosci/GTB_Substrate_Prediction.git
```

Set up environment:
```
cd GTB_Substrate_Prediction
conda env install --name gtb -f env.yml
ipython kernel install --user --name=gtb
```
Then open the notebook and run from below the "Generating Datasets" line!

Most of the data, like the pdb and secondary structure, is pre-computed and already downloaded from the databases, but if you'd like to recompute, just delete everything except the CSV_Data from the Data folder and rerun the notebook. If you'd like to run with your own dataset, simply replace the Data/CSV_Data/start.csv file with your own data (make sure the column formats match).

Contributor: Samantha Hennen https://github.com/samihennen 

Citing this work:
If you use the code or data in this package, please cite:
```
@article{D4DD00338A,
author ="Hennen, Samantha G. and Bomble, Yannick J. and Urbanowicz, Breanna R. and Bharadwaj, Vivek S.",
title  ="Decoding substrate specificity determining factors in glycosyltransferase-B enzymes – insights from machine learning models",
journal  ="Digital Discovery",
year  ="2025",
volume  ="4",
issue  ="8",
pages  ="2214-2228",
publisher  ="RSC",
doi  ="10.1039/D4DD00338A",
url  ="http://dx.doi.org/10.1039/D4DD00338A",
}
```
