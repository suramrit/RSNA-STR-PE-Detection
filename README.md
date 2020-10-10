# Highlights:

  #### Competition details: https://www.kaggle.com/c/rsna-str-pulmonary-embolism-detection/

  ## Whats in the dataset:
    - Csv files
    - Images 
    
  ## File descriptions
  - test  - all test images
  - train - all train images (note that your submission kernels will NOT have access to this set of images, so you must build your models elsewhere and          
           incorporate them into your submissions)
  - sample_submission.csv - contains rows for each UID+label combination that requires a prediction. Therefore it has a row for each image (for which you will be                             predicting the existence of a pulmonary embolism within the image) and row for each study+label that requires a study-level         
                            prediction.
  - train.csv - contains UIDs and all labels.
  - test.csv - contains UIDs.

  ## Images: 
  - The images are grouped in directories by study and series. They are in DICOM format, and contain additional metadata that may be relevant to the competition. Each image has a unique identifier - SOPInstanceUID.
  - The location for each image is given by: "<-StudyInstanceUID->/<-SeriesInstanceUID->/<-SOPInstanceUID->.dcm"
  
  ## CSV Files:  
  - train.csv contains the three UIDs noted above, and a number of labels. Some are targets which require predictions, and some are informational [See data fields below]
  - test.csv contains only the three UIDs. 
  
  ## What to predict:
  - Predicting a number of labels, at both the image and study level [See Evaluation at https://www.kaggle.com/c/rsna-str-pulmonary-embolism-detection/overview/evaluation for more details]
  
  ## Data Fields:  
     *todo : Label which are target fields
  - StudyInstanceUID - unique ID for each study (exam) in the data.
  - SeriesInstanceUID - unique ID for each series within the study.
  - SOPInstanceUID - unique ID for each image within the study (and data).
  - pe_present_on_image - image-level, notes whether any form of PE is present on the image.
  - negative_exam_for_pe - exam-level, whether there are any images in the study that have PE present.
  - qa_motion - informational, indicates whether radiologists noted an issue with motion in the study.
  - qa_contrast - informational, indicates whether radiologists noted an issue with contrast in the study.
  - flow_artifact - informational
  - rv_lv_ratio_gte_1 - exam-level, indicates whether the RV/LV ratio present in the study is >= 1
  - rv_lv_ratio_lt_1 - exam-level, indicates whether the RV/LV ratio present in the study is < 1
  - leftsided_pe - exam-level, indicates that there is PE present on the left side of the images in the study
  - chronic_pe - exam-level, indicates that the PE in the study is chronic
  - true_filling_defect_not_pe - informational, indicates a defect that is NOT PE
  - rightsided_pe - exam-level, indicates that there is PE present on the right side of the images in the study
  - acute_and_chronic_pe - exam-level, indicates that the PE present in the study is both acute AND chronic
  - central_pe - exam-level, indicates that there is PE present in the center of the images in the study
  - indeterminate -exam-level, indicates that while the study is not negative for PE, an ultimate set of exam-level labels could not be created, due to QA issues
  
  ## Relation between labels
  - The following flowchart shows the different relationships between the labels
  - There are four labels in the training set that are purely informational and require no predictions. 
      - QA Contrast 
      - QA Motion
      - True filling defect not PE
      - Flow artifact
  - They are not scored, but are meant to be used as helpers.
  - Acute PE is not an explicit label, but is implied by the lack of Chronic PE or Acute and Chronic PE.
  ![Flow](/repo_images/PE_label_flowchart.jpg)
