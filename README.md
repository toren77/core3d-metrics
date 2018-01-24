# JHU/APL pubgeo
JHU/APL is working to help advance the state of the art in geospatial computer vision by developing public benchmark data sets and open source software.
For more information on this and other efforts, please visit [JHU/APL](http://www.jhuapl.edu/pubgeo.html).

## GeoMetrics
 Performs metric analysis for 3D models. Initial metrics are described in the following paper:
 M. Bosch, A. Leichtman, D. Chilcott, H. Goldberg, M. Brown. “Metric Evaluation Pipeline for 3D Modeling of Urban Scenes”, ISPRS Archives, 2017 [pdf](https://www.int-arch-photogramm-remote-sens-spatial-inf-sci.net/XLII-1-W1/239/2017/isprs-archives-XLII-1-W1-239-2017.pdf). This is now hosted on GitHub to enable a community of developers to contribute improvements.

### Requirements
The following python3 libraries (and their dependencies) are required:
* gdal
* laspy
* matplotlib
* numpy
* scipy
* tk

Alternatively, you can use the provided docker [container](Dockerfile).

### GeoMetrics Usage
    python3 run_geometrics.py <AOI Configuration>
One of the first steps of the GeoMetrics tool is to align your dataset to the ground truth. This is performed using pubgeo's [ALIGN3D](https://github.com/pubgeo/pubgeo/#align3d) algorithm.
The algorithm then calculates metrics for 2D, 3D, and spectral classification against the ground truth.

#### Input
_AOI Configuration_ is a configuration file using python's ConfigParser that is further described in [aoi-config.md].
This configuration file informs GeoMetrics which files to analyze and what to compare against (ground truth). Additionally the config is
to toggle various software settings.

#### Example Output
    python3 run_geometrics.py aoi.config
This command would invoke the GeoMetrics library and perform metric analysis on
the test dataset provided by the aoi.config file. This analysis will also generate the following files (in place):
* < test dataset >_2d_metrics.txt
* < test dataset >_3d_metrics.txt

These files contain the determined metrics for completeness, correctness, f-score, Jaccard Index, Branching Factor, and the Align3d offsets.