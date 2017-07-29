## PhaceXL 2D

[![DOI](https://zenodo.org/badge/doi/10.5281/zenodo.825846.svg)](http://doi.org/10.5281/zenodo.825846)

PhaceXL_2D is a script for the generation of finite-thickness interface elements for 2D polycrystal microstructure modelling. It parses a 2D polycrystal microstructure mesh file generated using the [Neper](http://neper.sourceforge.net/) software package and modified using the [Phon](http://github.com/KristofferC/Phon) cohesive element generator and shrinks the existing grains by a predefined factor to create finite-thickness interface elements at the grain boundaries. If the original 2D polycrystal microstructure mesh is periodic, PhaceXL_2D retains mesh periodicity at the boundary of the modelling domain. The resulting mesh is exported in a format readable by Abaqus&#8482; software and can be used for finite-element analyses.

![Exemplary 2D polycrystal mesh segment](docs/example.jpg "Exemplary 2D polycrystal mesh segment with finite-thickness interface elements at grain boundaries")

To generate a 2D polycrystal microstructure mesh with finite-thickness interface elements at the grain boundaries, the following steps have to be followed:

1. Generate a 2D polycrystal microstructure mesh using [Neper](http://neper.sourceforge.net/).
2. Export the polycrystal mesh as well as the coordinates of the grain centroids.
3. Use [Phon](http://github.com/KristofferC/Phon) to insert zero-thickness cohesive elements at the grain boundaries.
4. Parse both files in PhaceXL_2D to generate finite-thickness interface elements at the grain boundaries.

![Exemplary 2D polycrystal mesh](docs/example_full.jpg "Exemplary 2D polycrystal mesh domain with finite-thickness interface elements at grain boundaries")

#### How to use the script:

Run [PhaceXL_2D](main/phaceXL_2D.py) using &nbsp; '*phaceXL_2D.py -i INPUTFILENAME -c CENTROIDFILENAME -p MPER -s SFACTOR*' &nbsp; from the command line. The following input parameters have to be specified:

 *INPUTFILENAME*: &nbsp; name of the file containing the polycrystal mesh and the cohesive elements generated by [Neper](http://neper.sourceforge.net/) and [Phon](http://github.com/KristofferC/Phon),  
 *CENTROIDFILENAME*: &nbsp; name of the file containing the coordinates of the grain centroids,  
 *MPER*:             &nbsp; indication whether the polycrystal microstructure mesh is periodic ('y') or (by default) non-periodic ('n'),  
 *SFACTOR*:          &nbsp; factor controlling the amount of shrinkage for each grain.  

PhaceXL_2D has been tested with [Python](http://www.python.org/downloads/) 2.6.5 and [NumPy](http://www.scipy.org/scipylib/download.html) 1.3.0. PhaceXL_2D is licensed under the [GNU General Public License](LICENSE.txt).
