# // geophysical_notes //

My collection of geophysical notes written as IPython notebooks.


# seismic petrophysics

Do magic things with well log data.

* [Seismic Petrophysics](http://nbviewer.ipython.org/github/aadm/geophysical_notes/blob/master/seismic_petrophysics.ipynb)
* [Seismic Petrophysics / interactive](http://nbviewer.ipython.org/github/aadm/geophysical_notes/blob/master/seismic_petrophysics_interactive.ipynb)
* [Rock physics modeling and templates](http://nbviewer.ipython.org/github/aadm/geophysical_notes/blob/master/rock_physics_modeling.ipynb)


#### support data for "seismic petrophysics"

* `well_2*.txt`: raw log data from Well 2 of [Quantitative Seismic Interpretation (QSI)](https://pangea.stanford.edu/researchgroups/srb/resources/books/quantitative-seismic-interpretation)
* `qsiwell2.csv`: assembled all the logs from various files
* `qsiwell2_frm.csv`: qsiwell2 + fluid replaced elastic logs
* `qsiwell2_augmented.csv`: barebones well data, only Ip, Vp/Vs and LFC (litho-fluid class log)
* `qsiwell2_synthetic.csv`: synthetic data generated through Monte Carlo simulation, same logs as in `qsiwell2_augmented.csv` (Ip, Vp/Vs and LFC)
* `qsiwell2_dataprep.py`: Python script to assemble all the original QSI files


# seismic stuff

How to load and display SEG-Y files, plus some simple ways to play with the data, e.g. extracting amplitude informations, adding noise & filtering. Also, a notebook entirely dedicated to wedge modeling.

* [Seismic data in Python](http://nbviewer.ipython.org/github/aadm/geophysical_notes/blob/master/seismic_data_in_python.ipynb)
* [Amplitude extraction](http://nbviewer.ipython.org/github/aadm/geophysical_notes/blob/master/seismic_amplitude_extraction.ipynb)
* [Wedge modeling for variable angles of incidence](http://nbviewer.ipython.org/github/aadm/geophysical_notes/blob/master/wedge_modeling.ipynb)
* [Notes on spectral decomposition](http://nbviewer.ipython.org/github/aadm/geophysical_notes/blob/master/notes_spec_dec.ipynb)
* [Top Heimdal map, or how to reproduce figure 1 from Avseth et al., 2001](http://nbviewer.ipython.org/github/aadm/geophysical_notes/blob/master/top_heimdal_map.ipynb)
* [AVO projections](http://nbviewer.ipython.org/github/aadm/geophysical_notes/blob/master/avo_projections.ipynb)
* [How to calculate AVO attributes](http://nbviewer.ipython.org/github/aadm/geophysical_notes/blob/master/avo_attributes.ipynb)

#### support data for "seismic stuff"

* `16_81_PT1_PR.SGY`, `16_81_PT2_PR.SGY`, `16_81_PT3_PR.SGY`, `31_81_PR.SGY`: 2D lines in SEGY format from the [USGS Alaska dataset](http://energy.usgs.gov/GeochemistryGeophysics/SeismicDataProcessingInterpretation/NPRASeismicDataArchive.aspx)
* `3d_farstack.sgy`, `3d_nearstack.sgy`: 3D cubes from the QSI dataset (see above)
* `Top_Heimdal_subset.txt`: interpreted horizon for the QSI near and far angle cubes
* `segypy.py`: modified from the [original](https://github.com/rob-smallshire/segpy) to make it self-contained and portable (basically I have inserted `header_definition.py`, `ibm_float.py`, `revisions.py`, `trace_header_definition.py` into `segypy.py`)


## notes on running python

I would recommend either [Enthought's Canopy Express]((https://www.enthought.com/products/canopy/))or [Anaconda](https://www.continuum.io/why-anaconda). I am now using Anaconda both on my work PC and my home computer (an Apple laptop) but I have also been happy with Canopy. There must be some difference between the two but for all practical means they are equivalent.

There is also a third solution (the _homemade solution_) which works only on Apple computers and not really recommended unless you are a little bit more adventurous. It has the advantage of being a barebone installation with minimal impact on disk space; full instructions here: <http://penandpants.com/2013/04/04/install-scientific-python-on-mac-os-x/>. It involves installing [Homebrew](http://brew.sh) on your Mac (which is a great [package manager](http://en.wikipedia.org/wiki/Package_manager) essential for anybody tinkering with code and unix-like applications on Macs). Then you do everything through [IPython or Jupyter notebooks](http://jupyter.org/), perhaps in conjunction with a modern (and free!) editor like [Atom](https://atom.io/) to write longer codes and preview your markdown.

However, even if you're tight in (drive) space there is an easier solution than the above _homemade_ recipe, and that involves once again the good folks at Continuum that have created [miniconda](http://conda.pydata.org/miniconda.html) -- highly recommended!

### using SEG-Y data

To read and write SEG-Y data in Python you need some library like  [ObsPy](http://obspy.org) or [Segpy](https://github.com/sixty-north/segpy).

I have included in this repo [a modified version of Segpy](https://github.com/aadm/geophysical_notes/blob/master/segypy.py) where I have simply collected all the scattered files of the original module (`segypy.py`, `header_definition.py`, `ibm_float.py`) into a single python file (`segypy.py`).

(Note added February 2016)

Until recently my favourite library was Segpy but recently I have had trouble reading a large (10Gb) SEG-Y exported from Petrel and only managed to read it using ObsPy. ObsPy has also matured to v1.0 so I would recommend it now-- if only for its SEG-Y support (what I didn't like before was simply the concept of using a large library aimed at research seismologists that does too many things that I don't use; but yes you could say that's true also for the way I use Numpy!).

I also have to add that Segpy has been developed in the last months and I have not used this new version yet (there is a rather interesting "extract_dataset_3d" in the github repo that looks interesting).
