A method to classify predominant pitch contours into vocal and instrumental (non-vocal) ones. 

It extends the method of 

Rachel M Bittner, Justin Salamon, Slim Essid, and Juan P Bello, �Melody extraction by contour classifi- cation,� in Proc. ISMIR, pp. 500�506

by adding contour fluctuation features. 
Each pitch contour is characterized by the baseline salience features + timbre- and pitch-fluctuation features


Usage:
------------------------

first set only one of Parameters.medleyDb, Parameters.datasetIKala or Parameters.for_makam to True

1) #extract contours with essentia: 
`python ~/workspace/SourceFilterContoursMelody/src/main_contour_extraction.py ~/Documents/iKala/  $PATH_CONTOURS 1`

NOTE: the extension pitch.ctr is same for contours with or without added timbre features
NOTE: Parameters.contour_URI

or copy them
`cp /home/georgid/Documents/iKala/Conv_mu-1_G-0_LHSF-0_pC-27.56_pDTh-0.9_pFTh-0.9_tC-100_mD-200_vxTol-0.2/*.pitch.ctr  $PATH_CONTOURS`


2) load pre-extracted contours and add fluctuation features 

`python ~/workspace/SourceFilterContoursMelody/src/main_contour_extraction.py ~/Documents/iKala/  $PATH_CONTOURS 2`



3) classify
### classify SALomon's features:
`python ~/workspace/SourceFilterContoursMelody/src/contour_classification/run_contour_training_melody_extraction.py $PATH_CONTOURS 1 0 0`

### classify SALomon's features + fluctogram:
`python ~/workspace/SourceFilterContoursMelody/src/contour_classification/run_contour_training_melody_extraction.py $PATH_CONTOURS 1 1 0`

### classify SALomon's features + VV:
`python ~/workspace/SourceFilterContoursMelody/src/contour_classification/run_contour_training_melody_extraction.py $PATH_CONTOURS 1 0 1`
if experimenting with diff feature parameters:  set Parameters.use_<featureName>_for_classification  << used in src.contour_classification.contour_utils.getFeatureInfo() >>


4) evaluate 
`src.contour_classification.run_contour_training_melody_extraction.eval`




Useful tools: 
-------------

see test directory
### plot interactively contours:  

plot_contours_interactive(contour_data, dset_annot_dict[track], track)

### and plot the decoded melody 
plot_decoded_melody


### extract features with already extracted contour:
test_timbre_features

compute_and_plot_harmoncis

### sonify the harmonics of extracted contours

python ~/workspace/SourceFilterContoursMelody/src/main_contour_extraction.py ~/Documents/iKala/ $PATH_CONTOURS 3  


### to use vocal variance feature extraction code in MATLAB:
	set Parameters.features_MATLAB = True
	
	
	# extract feat. matlab.. Bernhard Lehner
	in matlab in /home/georgid/Documents/svd
	then extractSVD2015features
