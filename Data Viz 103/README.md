# Content for Data Viz 103 - Interactive Data Visualization

## PyQtGraph

[PyQtGraph](www.pyqtgraph.org) is a plotting library that bridges the gap between numpy and scipy, to Qt, the cross-platform application development framework.  While the static plot capabilities of PyQtGraph are nowhere near as sophisticated as matplotlib, seaborn, altair or other frameworks, the area that PyQtGraph accelerates in is interactivity.  It handles mouse events (zoom, pan, and in the case of 3D, rotate) with ease.  Furthermore, it is very high performance, so you can throw a lot of data points at it, and the plots will update quickly.  This is very beneficial in cases where someone is attempting to plot live sensor readings, or plot data that is rapidly changing.

An example application is bundled with the library that can be executed with `python -m pyqtgraph.examples` which shows a list of examples, along with the code to generate the example, and a run button.  The window showing the code allows the user to modify the code, allowing individuals to experiment with changing code and seeing what happens.

### Dependencies

PyQtGraph has a minimal set of required dependencies, and a series of optional dependencies for extra functionality.  

#### Required

What is required is a set of Qt bindings, from Qt 5.12 or newer.  We recommend the current Qt6 bindings from the PySide6 library.  Furthermore, PyQtGraph requires the use of NumPy, which we recommend 1.20+ due to [SIMD optimizations])https://numpy.org/devdocs/reference/simd/simd-optimizations.html).

```text
pyside6
numpy
```

#### Optional

To use the image processing capability that PyQtGraph offers, end users must install `scipy`.  PyQtGraph offers `matplotlib` color-maps and export functionality if it is installed; and if `colorcet` is installed, the color`maps from there are also available.

If a user wants to plot in 3D space, `pyopengl` is required.  Note, on macOS 11+, users are required to use Python 3.9.1+ for this to work.

For higher image processing workloads, PyQtGraph has optional support for CUDA.  This is only available on machines with CUDA framework installed and the appropriate `cupy` package (Windows users require `cupy`/`CUDA` >= 11.1).

For larger datasets, PyQtGraph offers support for the HDF5 binary format. using `h5py` library.

### Compatibility Issues

PyQtGraph adopts [NEP-29](https://numpy.org/neps/nep-0029-deprecation_policy.html), which at the time of this writing, it supports NumPy 1.17+, and Python 3.7+.  In terms of Qt bindings, PyQtGraph requires Qt 5.12+.  

The Qt version requirement can be in conflict if an end user is using a `conda` and has `matplotlib` installed from the `main` channel (which installs PyQt5 5.9, which PyQtGraph attempts, but fails to use).

Another source of compatibility issues is for macOS 11+ users, attempting to use the pyopenGL functionality (for 3D plots), this requires Python 3.9.1+.

## Get Started

```bash
python3 -m venv .venv
source .ven/bin/activate
pip install --upgrade pip setuptools wheel
pip install numpy pyside6 scipy pyqtgraph
python -m pyqtgraph.examples
```

Or on Windows

```powershell
python3 -m venv .venv
.venv/Scripts/activate
python -m pip install --upgrade pip setuptools wheel
python -m pip install numpy scipy pyside6 pyqtgraph
python -m pyqtgraph.examples
```
