# Simons CMAP Data Submission: <br/> File Structure

<a id="toc"></a>
## Table of Contents
1. <a href="#introduction">Introduction</a>
1. <a href="#data_sheet">Data Sheet</a>
    * <a href="#time">time</a>
    * <a href="#lat">lat</a>
    * <a href="#lon">lon</a>
    * <a href="#depth">depth</a>
    * <a href="#vars">vars</a>
1. <a href="#dataset_metadata">Dataset Metadata</a>
    * <a href="#dataset_short_name">dataset_short_name</a>
    * <a href="#dataset_long_name">dataset_long_name</a>
    * <a href="#dataset_version">dataset_version</a>
    * <a href="#dataset_release_date">dataset_release_date</a>
    * <a href="#dataset_make">dataset_make</a>
    * <a href="#dataset_source">dataset_source</a>
    * <a href="#dataset_distributor">dataset_distributor</a>
    * <a href="#dataset_acknowledgement">dataset_acknowledgement</a>
    * <a href="#dataset_history">dataset_history</a>
    * <a href="#dataset_description">dataset_description</a>
    * <a href="#dataset_references">dataset_references</a>
    * <a href="#climatology">climatology</a>
    * <a href="#cruise_names">cruise_names</a>

1. <a href="#variable_metadata">Variable Metadata</a>
    * <a href="#var_short_name">var_short_name</a>
    * <a href="#var_long_name">var_long_name</a>
    * <a href="#var_sensor">var_sensor</a>
    * <a href="#var_unit">var_unit</a>
    * <a href="#var_spatial_res">var_spatial_res</a>
    * <a href="#var_temporal_res">var_temporal_res</a>
    * <a href="#var_discipline">var_discipline</a>
    * <a href="#visualize">visualize</a>
    * <a href="#var_keywords">var_keywords</a>    
    * <a href="#var_comment">var_comment</a>

1. <a href="#bibliography">Bibliography</a>
    * [References](#references)



<br/><br/>
<br/><br/>
<br/><br/>

------------------------------------------
<a id="introduction"></a>
## Introduction 
<div style="text-align: right"><a href="#toc" title="Table of Contents">Table of Contents</a></div>   
This document describes the specifications of the data and metadata fields required for submitting datasets to the Simons CMAP database. As long as the required fields are provided the submitted data can be in any file format such as netCDF, plain text file, CSV, or Excel files. For simplicity, we have created an empty dataset template in Excel format which can be found [here](https://github.com/simonscmap/DBIngest/raw/master/template/datasetTemplate.xlsx). Please use this template to load and submit your dataset. The data and metadata field names (e.g. time, lat, lon, short_name, long_name, ...) used in the template file have been inspired by the CF and COARDS naming conventions [<a href="#ref1">1</a>, <a href="#ref1">2</a>, <a href="#ref1">3</a>].


The CMAP data template consists of three sheets: data, dataset metadata, and variable metadata. Data is stored in the first sheet called “data”. The second sheet stores the dataset metadata and is called “dataset_meta_data”. Metadata associated with the variables in the dataset are entered in the third sheet, “vars_meta_data”. All columns are required unless specified otherwise. Below are a few example datasets that have been prepared using the specifications described in this document:

* [SeaFlow](https://github.com/simonscmap/DBIngest/raw/master/template/SeaFlow_example.xlsx)
* [Gradients 1 Fluormetric Chl](https://github.com/simonscmap/DBIngest/raw/master/template/Gradients1-KOK1606-FluorometricChlorophyll_2020-03-03_V1.1_example.xlsx)
* [Gradients 1 Cobalamin](https://github.com/simonscmap/DBIngest/raw/master/template/KOK1606_Gradients1_Cobalamin_example.xlsx)
* [Gradients 3 Underway CTD](https://github.com/simonscmap/DBIngest/raw/master/template/KM1906_Gradients3_uwayCTD_example.xlsx)

<br/><br/>
<br/><br/>
<br/><br/>



------------------------------------------
<a id="data_sheet"></a>
## Data Sheet
<div style="text-align: right"><a href="#toc" title="Table of Contents">Table of Contents</a></div> 

| time   |      lat     |  lon |  depth [if exists] | var<sub>1</sub> | ... | var<sub>n</sub>
|:----------:|:-------------:|:------:|:------:|:------:|:------:|:------:|
| example: 2016-5-01T15:02:00 | 25  | -158 | 5 | value | ... | value |

All of the data points are stored in the "Data" sheet. Every single data point must have time and location information. The exact name and order of the time and location columns are shown in the table above. If a dataset does not have depth values (sea surface measurements) you may remove the depth column. The columns var<sub>1</sub>  ...  var<sub>n</sub> represent the dataset variables (measurements). Please rename var<sub>1</sub>  ...  var<sub>n</sub> to appropriate names. The format of "time", "lat", "lon", and "depth" columns are described in the following sections. Please review the example datasets listed in the <a href="#introduction">introduction</a> for more detailed information.
<br/><br/>

<a id="time"></a>
+ **time<sup>*</sup>**<br/>
This column holds datetime values with the following format: %Y-%m-%dT%H:%M:%S<br/>
The date and time sections are separated by a "T" character.<br/>
Example: 2010-02-09T18:15:00
    * Year (%Y) is a four-digit value: example 2010
    * Month (%m) is a two-digit value: example 02 (for Feburary)
    * Day (%d) is a two-digit value: example 09 
    * Hour (%H) is a two-digit value from 00 to 23: example 18 
    * Minute (%M) is a two-digit value from 00 to 59: example 15 
    * Second (%S) is a two-digit value from 00 to 59: example 00
    * Time zone: UTC 
<br/><br/>

<a id="lat"></a>
+ **lat<sup>*</sup>**<br/>
This column holds the latitude values with the following characteristics:<br/>
    * Type: Numeric values from -90 to 90
    * Format: Decimal (not military grid system)
    * Unit: degree North 
<br/><br/>

<a id="lon"></a>
+ **lon<sup>*</sup>**<br/>
This column holds the longitude values with the following characteristics:<br/>
    * Type: Numeric values from -180 to 180
    * Format: Decimal (not military grid system)
    * Unit: degree East 
<br/><br/>

<a id="depth"></a>
+ **depth**<br/>
This column holds the depth values with the following characteristics:<br/>
    * Type: Positive numeric values. It is 0 at surface and increases at lower depth levels.
    * Format: Decimal
    * Unit: meter 
<br/><br/>

<a id="vars"></a>
+ **var<sub>1</sub>  ...  var<sub>n</sub>**<br/>
These columns represent the dataset variables (measurements). Please rename 
them to appropriate names. Please do not include units in these columns; units are recorded in the ["vars_meta_data"](#variable-metadata) sheet. For missing values, meaning the instances where data was not taken, leave the cell empty. Please review the example datasets listed in the <a href="#introduction">introduction</a> for more information.

<br/><br/>
<br/><br/>
<br/><br/>





------------------------------------------
<a id="dataset_metadata"></a>
## Dataset Metadata
<div style="text-align: right"><a href="#toc" title="Table of Contents">Table of Contents</a></div>   
This sheet holds a list of top-level attributes about the dataset such as the dataset name and description. Below are the list of these attributes along with their descriptions. Please review the example datasets listed in the <a href="#introduction">introduction</a> for more information.
<br/><br/>

<a id="dataset_short_name"></a>
+ **dataset_short_name<sup>*</sup>**<br/>
This name is meant to be used in programming codes and scripts. So it should only contain a combination of letters, numbers, and underscores. Do not use space, dash, or special characters such as <, +, %, etc. It must be shorter than 50 characters and is a required field. <br/> 

    * Required: Yes
    * Constraint: Less than 50 characters
<br/><br/>    

<a id="dataset_long_name"></a>
+ **dataset_long_name<sup>*</sup>**<br/>
 A descriptive and human-readable name for the dataset. This name will present your dataset in the CMAP catalog (<a href="#fig_dataset_long_name_cat">Fig.1</a>), visualization search dialog (<a href="#fig_dataset_long_name_viz">Fig.2</a>). Any Unicode character can be used here, but please avoid names longer than 200 characters as they might get trimmed while displayed on graphical interfaces. Please refer to <a href="#dataset_description">dataset_description</a>  in case you would like to add a full textual description (with not length limits) for your dataset. 
 <br/>  

    * Required: Yes
    * Constraint: Less than 200 characters
<br/><br/>    

<figure>
  <img id="fig_dataset_long_name_cat" src="./pics/dataset_long_name_cat.png" alt="Dataset Long_name in Catalog">
  <figcaption>Figure 1. A sample dataset shown in the Simons CMAP catalog. The "dataset_long_name" is enclosed in the red rectangle.</figcaption>
</figure>

<figure>
  <img id="fig_dataset_long_name_viz" src="./pics/dataset_long_name_viz_search.png" alt="Dataset Long_name in Visualization Page">
  <figcaption>Figure 2. The "dataset_long_name" appears in the visualization page search dialog.</figcaption>
</figure>

<br/><br/>  


<a id="dataset_version"></a>
+ **dataset_version<sup>*</sup>**<br/>
Please assign a version number or an identifier to your dataset such as "1.0.0" or "ver 1". Version identifiers will help tracking the evolution of a dataset over time. <br/>  

    * Required: Yes
    * Constraint: Less than 50 characters
    * Example: 1.0
<br/><br/>    


<a id="dataset_release_date"></a>
+ **dataset_release_date<sup>*</sup>**<br/>
Indicates the release date of the dataset. If your dataset has been previously published or released publicly, please specify that date. Otherwise, note the date the data was submitted to CMAP. <br/>

    * Required: Yes
    * Constraint: Less than 50 characters
    * Example: 1.0
<br/><br/>  


<a id="dataset_make"></a>
+ **dataset_make<sup>*</sup>**<br/>
This is a required field specifying a broad production category for the dataset (also referred to as `dataset make`). It can only have a single value from a fixed set of options (observation, model, assimilation, laboratory) which are described below. This field will greatly help to find the data at CMAP by categorizing them according to their make class. Please contact us if you believe your dataset make is not consistent with any of the values below:<br/>

    * **Observation**: refers to any in-situ or remote sensing measurements such as measurements made during a cruise expedition, data from an in-situ sensor, or satellite observations. Observations made at laboratory settings (culture experiments) have their distinct category and do not fall in this category.

    * **Model**: refers to the outputs of the numerical simulations.  

    * **Assimilation**: refers to the products that are a blend of observations and numerical models.

    * **Laboratory**: refers to the observations made in a laboratory setting such as culture experiment results.
<br/><br/>  


<a id="dataset_source"></a>
+ **dataset_source<sup>*</sup>**<br/>
Specifies the group and/or the institute name of the data owner(s). It can also include any link (such as a website) to the data producers. This information will be visible in the CMAP catalog as shown in the figure below. Also, dataset_source will be annotated to any visualization made using the dataset (<a href="#fig_dataset_source_viz">Fig. 4</a>). This is a required field and its length must be less than 100 characters. <br/>

    * Required: Yes
    * Constraint: Less than 100 characters
    * Example: Armbrust Lab, University of Washington
<br/><br/>  

<figure>
  <img id="fig_dataset_source_cat" src="./pics/dataset_source_cat.png" alt="Dataset Source in Catalog">
  <figcaption>Figure 3. A sample dataset shown in the Simons CMAP catalog. The "dataset_source" is enclosed in the red rectangle.</figcaption>
</figure>

<figure>
  <img id="fig_dataset_source_viz" src="./pics/dataset_source_viz.png" alt="Dataset Source in Visualizations">
  <figcaption>Figure 4. The "dataset_source" appears in visualization made using the corresponding dataset (enclosed in the red rectangle).</figcaption>
</figure>

<!--- Comment For Raphael: data source in plots (see figure above) seem to be data distributor not data source. Ask Mike to correct it. -->
<br/><br/> 


<a id="dataset_distributor"></a>
+ **dataset_distributor**<br/>
If your dataset has already published by a data distributor provide a link to the data distributor. Otherwise, leave this field empty. This is not a required field.<br/>

    * Required: No (optional)
    * Constraint: Less than 100 characters
    * Example: http://marine.copernicus.eu/
<br/><br/>  


<a id="dataset_acknowledgement"></a>
+ **dataset_acknowledgement**<br/>
Specify how your dataset should be acknowleged. You may mention your funding agency, grant number, or you may ask the CMAP users to acknowledge your dataset via a certain phrase. Dataset acknowlegment will be visible in the catalog page (<a href="#fig_dataset_ack_cat">Fig. 5</a>). This is not a required field.<br/>

    * Required: No (optional)
    * Constraint: No length limits    
<br/><br/>  
    
<figure>
  <img id="fig_dataset_ack_cat" src="./pics/dataset_ack_cat.png" alt="Dataset Acknowledgment in Catalog">
  <figcaption>Figure 5. A sample dataset shown in the Simons CMAP catalog. The "dataset_acknowledgement" is enclosed in the red rectangle.</figcaption>
</figure>


<br/><br/> 


<a id="dataset_history"></a>
+ **dataset_history**<br/>
Use this field in case your dataset has evolved over time and you wish to add notes about the history of your dataset. Otherwise, leave this field empty. This is not a required field.
<br/><br/>  


<a id="dataset_description"></a>
+ **dataset_description<sup>*</sup>**<br/>
Include any description that you think will guide the reader to better understand your dataset. This can involve information about data acquisition, processing methods, figures, and links to the external contents. This field acts as the dataset documentation is visible in the Simons CMAP catalog (<a href="#fig_dataset_description_cat">Fig. 6</a>). This field is required.<br/>  

    * Required: Yes
    * Constraint: No length limits
<br/><br/>    

<figure>
  <img id="fig_dataset_description_cat" src="./pics/dataset_description_cat.png" alt="Dataset description in Catalog">
  <figcaption>Figure 6. A sample dataset shown in the Simons CMAP catalog. The "dataset_description" is accessible using the "Dataset Details" button, enclosed in the red rectangle.</figcaption>
</figure>

<br/><br/>  


<a id="dataset_references"></a>
+ **dataset_references**<br/>
List any publications or documentation that one may cite in reference to the dataset. If there are more than one references, please put them in separate cells under the dataset_reference column. Leave this field empty if there are no publications associated with this dataset. This is not a required field. 
<br/><br/>  


<a id="climatology"></a>
+ **climatology**<br/>
This is a flag indicating whether the dataset represents a climatological product. If your dataset is a climatological product fill this field with "1". Otherwise, leave this field blank. This is not a required field.
<br/><br/>  


<a id="cruise_names"></a>
+ **cruise_names**<br/>
If your dataset represents measurements made during a cruise expedition (or expeditions), provide a list of cruise official names here. In case your dataset is associated with more than one cruise, please put them in separate cells under the cruise_names column. If the cruises have any nicknames, please include them too. Leave this field blank if your dataset is not associated with a cruise expedition. This is not a required field.<br/>

    * Required: No (optional)
    * Constraint: No length limits
    * Example: KOK1606, Gradients 1
<br/><br/>  



<br/><br/>
<br/><br/>
<br/><br/>




------------------------------------------

<a id="variable_metadata"></a>
## Variable Metadata
<div style="text-align: right"><a href="#toc" title="Table of Contents">Table of Contents</a></div>  
A dataset can contain multiple different measurements (variables). This sheet (labeled as "vars_meta_data") holds a list of top-level attributes about these variables such as the variable name, unit, and description. Each variable along with its attributes (metadata) are stored in separate rows. Below is the list of these attributes along with their descriptions. Please review the example datasets listed in the <a href="#introduction">introduction</a> for more information.
<br/><br/>



<a id="var_short_name"></a>
+ **var_short_name<sup>*</sup>**<br/>
This name is meant to be used in programming codes and scripts. So it should only contain a combination of letters, numbers, and underscores. Do not use space, dash, or special characters such as <, +, %, etc.  `var_short_name` will be seen in the CMAP catalog (<a href="#fig_var_short_name_cat">Fig. 7</a>), and will appear as the title of the generated figures (<a href="#fig_var_short_name_viz">Fig. 8</a>). This a required field and must be shorter than 50 characters. <br/> 

    * Required: Yes
    * Constraint: Less than 50 characters
<br/><br/>    

<figure>
  <img id="fig_var_short_name_cat" src="./pics/var_short_name_cat.png" alt="Variable short name in catalog">
  <figcaption>Figure 7. A sample dataset shown in the Simons CMAP catalog. The "var_shot_name" is highlighted in the red rectangle.</figcaption>
</figure>


<figure>
  <img id="fig_var_short_name_viz" src="./pics/viz_short_name.png" alt="Variable short name in a figure">
  <figcaption>Figure 8. A sample figure generated in the Simons CMAP catalog. The "var_shot_name" appears at the figure's title and is highlighted in the red rectangle.</figcaption>
</figure>

<br/><br/>    



<a id="var_long_name"></a>
+ **var_long_name<sup>*</sup>**<br/>
 A descriptive and human-readable label for the variable in accordance with the CF and COARDS conventions [<a href="#ref1">1</a>, <a href="#ref1">2</a>, <a href="#ref1">3</a>]. This name will present your variable in the CMAP catalog (<a href="#fig_var_long_name_cat">Fig. 9</a>), visualization search dialog (<a href="#fig_var_long_name_search_viz">Fig. 10</a>). `var_long_name` can contain any unicode character, but please avoid names longer than 200 characters as they might get trimmed while displayed on graphical interfaces. Please refer to <a href="#var_comment">var_comment</a> in case you would like to add a full textual description (with not length limits) for your variable. 
 <br/>  

    * Required: Yes
    * Constraint: Less than 200 characters
<br/><br/>    

<figure>
  <img id="fig_var_long_name_cat" src="./pics/var_long_name_cat.png" alt="Variable long name in catalog">
  <figcaption>Figure 9. A sample dataset shown in the Simons CMAP catalog. The "var_long_name" is highlighted in the red rectangle.</figcaption>
</figure>

<figure>
  <img id="fig_var_long_name_search_viz" src="./pics/var_long_name_viz_search.png" alt="var long name in visualization page">
  <figcaption>Figure 10. The "var_long_name" appears in the visualization page search dialog.</figcaption>
</figure>

<br/><br/>  



<a id="var_sensor"></a>
+ **var_sensor<sup>*</sup>**<br/>
This is a required field that refers to the instrument used to produce the measurements such as `CTD`, `fluorometer`, `flow cytometer`, `sediment trap`, etc. If your dataset is the result of a field expedition but you are not sure about the name of the instrument used for the measurements, use the term "in-situ" to fill out this field. This field will significantly help to find and categorize data achieved using a similar class of instruments. `var_sensor` will be visible in the Simons CMAP catalog.

<br/><br/>  


<a id="var_unit"></a>
+ **var_unit**<br/>
Specifies the variable's unit, if applicable. Leave this field blank if your variable is unitless (e.g. "station numbers" or "quality flags"). It may contain unicode characters such as subscripts and superscripts. `var_unit` will be visible in the Simons CMAP catalog (see <a href="#fig_var_long_name_cat">Fig. 9</a>) and in the generated visualizations (see <a href="#fig_var_short_name_viz">Fig. 8</a>). This field is not required.<br/>  

    * Required: No (optional)
    * Constraint: Less than 50 characters
    * Example: ul L<sup>-1</sup>
<br/><br/>    



<a id="var_spatial_res"></a>
+ **var_spatial_res<sup>*</sup>**<br/>
Specifies the spatial resolution of the variable. Typically, gridded products have uniform spatial spacing (such as 0.25&deg; X 0.25&deg;) while field expeditions do not have a regular spatial resolution. If your variable does not have a regular spatial resolution, use the term "irregular" to fill out this field. Note that if samples are taken at a series of distinct but spatially-non-uniform stations, the spatial resolution is considered irregular. `var_spatial_res` may contain unicode characters such as degree symbol ( &deg; ) and will be visible in the Simons CMAP catalog (see <a href="#fig_var_long_name_cat">Fig. 9</a>). This field is required.<br/>  

    * Required: Yes
    * Constraint: Less than 50 characters
    * Example: irregular
<br/><br/>    



<a id="var_temporal_res"></a>
+ **var_temporal_res<sup>*</sup>**<br/>
Specifies the temporal resolution between the subsequent measurements (such as daily, hourly, 3-minutes, etc). Typically field expedition measurements do not have a regular temporal spacing in which case you may use the term "irregular" to fill out this field. `var_temporal_res` will be visible in the Simons CMAP catalog (see <a href="#fig_var_long_name_cat">Fig. 9</a>). This field is required.<br/>  

    * Required: Yes
    * Constraint: Less than 50 characters
    * Example: irregular
<br/><br/>    



<a id="var_discipline"></a>
+ **var_discipline<sup>*</sup>**<br/>
Indicates in which disciplines (such as Physics, Biology ...) this variable is commonly studied. You can specify more than one discipline. `var_discipline` will be visible in the Simons CMAP catalog (referred to as "Study Domain" in <a href="#fig_var_long_name_cat">Fig. 9</a>). This field is required.<br/>  

    * Required: Yes
    * Constraint: Less than 100 characters
    * Example: BioGeoChemistry
<br/><br/>    



<a id="visualize"></a>
+ **visualize**<br/>
This is a flag field and can only be 0 or 1. Fill this field by 1, if you think this variable can be visualized by Simons CMAP. In principle, any variable with numeric values can be visualized while variables with string values, station numbers, or quality flags may not be the best candidates for visualization in CMAP. Please consult with the data curation team if you have any questions. This is not a required field. <br/>  
<br/><br/>    


<a id="var_keywords"></a>
+ **var_keywords<sup>*</sup>**<br/>
Every single variable in CMAP is annotated with a range of semantically related keywords making the variable a lot more findable. For example, if one looks for "PO4" a list of all phosphate data are retrieved even if they are not named "PO4". Similarly, if one searches for "MIT", CMAP returns all variables generated by MIT groups, or if one looks for "model" it should only return model outputs. These "semantic" searches are made possible using the keywords that are added to each variable. We would like to have keywords to cover all of the following areas (if applicable). Please keep in mind that you may add as many keyword as you wish to a variable; there is no limit to the number of keywords. The keywords are case-insensetive and you may add/remove them at any point (even after data ingestion). This is a required field. 

    * Alternative names: other official, unofficial, abbreviation, technical (or jargon) names or notations associated with the variable. <br/> 
    Examples: Nitrate, NO3, NO_3

    * Method and Instrument: Keywords related to the method and instruments used for the variable measurements. <br/>
    Examples: observation, in-situ, model, satellite, remote sensing, cruise, CTD, cytometry, ....<br/><br/>
    Note these keywords are not mutually exclusive. For example, a CTD temperature measurement during a cruise can have all of the following keywords: observation, in-situ, cruise, CTD

    * Data Producers: Keywords associated with the lead scientist/lab name/institute name.<br/> 
    Examples: UW, University of Washington, Virginia Armbrust, Ginger

    * Cruise: The official/unoffical name of the cruise(s) during which the variable has been measured, if applicable.<br/> 
    Examples: KOK1606, Gradients_1, diel

    * Project name: If your data are in the context of a project, includ the project name.<br/> 
    Examples: HOT, Darwin, seaflow

<br/><br/>    


<a id="var_comment"></a>
+ **var_comment**<br/>
Use this field to communicate any detailed information about this particular variable with the users. `var_comment` is visible in the Simons CMAP catalog (<a href="#fig_var_comment_cat">Fig. 11</a>). This field is not required.<br/>  

    * Required: No (optional)
    * Constraint: No length limits
<br/><br/>    

<figure>
  <img id="fig_var_comment_cat" src="./pics/var_comment_cat.png" alt="Variable description in Catalog">
  <figcaption>Figure 11. A sample dataset shown in the Simons CMAP catalog. The "var_commentn" is accessible using the "Comment" button, highlighted in the red rectangle.</figcaption>
</figure>

<br/><br/> 




------------------------------------------

<a id="bibliography"></a>
## Bibliography
<div style="text-align: right"><a href="#toc" title="Table of Contents">Table of Contents</a></div>   

### References
1. <a id="ref1"></a>[NetCDF Climate and Forecast (CF) Metadata Conventions](http://cfconventions.org/cf-conventions/cf-conventions.html)
2. <a id="ref2"></a>[Conventions for the standardization of NetCDF files](https://ferret.pmel.noaa.gov/noaa_coop/coop_cdf_profile.html)
3. <a id="ref3"></a>[COARDS NetCDF Conventions](https://ferret.pmel.noaa.gov/Ferret/documentation/coards-netcdf-conventions)