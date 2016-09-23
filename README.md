# CDCS

CDCS (Cone Decomposition Conic Solver) is an open-source MATLAB&reg; solver for sparse conic programs with partially decomposable conic constraints. CDCS implements the alternating direction method of multipliers (ADMM) 
described in on our paper [_Fast ADMM for Semidefinite Programs with Chordal Sparsity_](https://arxiv.org/pdf/1609.06068v1.pdf).

**Current version:** 1.0


## Contents
* [Description](#Description)
* [Quick start](#QuickStart)
* [How to cite](#References)
* [Licence](#Licence)
* [Contact us](#Contacts)


## Description<a name="Description"></a>

CDCS solves in the standard primal and dual vectorized forms

		minimize 	c'x						maximize 	b'y
	(1)	subject to	Ax = b,				(2)	subject to	c - A'y = z,	
					x \in K								z \in K*

where the conic constraint `x \in K` are _partially decomposable_. This means that
`x \in K` can be replaced by `p` smaller conic constraints `x_1 \in K_1`, ..., 
`x_p \in K_p`, where `x_1`, ..., `x_p` are (possibly not-disjoint) subsets of the
original optimization variable `x`.

CDCS supports cartesian products of the following cones:

* R^n (free variables)
* Non-negative orthant
* Second-order cone
* Positive semidefinite cone

Currently, CDCS only decomposes semidefinite cones characterized by a chordal 
sparsity pattern. The other supported cone types are not decomposed. 
This means that CDCS is most suitable for large sparse semidefinite programs (SDPs),
although it can be used for any conic program over the supported cones.



## Quick start<a name="QuickStart"></a>

To install CDCS, simply run the installer script at the MATLAB&reg; command line:

	>> cdcsInstall;

To test your installation, run 

	>> cdcsTest;
	
CDCS is called with the syntax

	>> [x,y,z,info] = cdcs(At,b,c,K,options);
	
where `At` is the transpose of the matrix `A` in problems (1)-(2) above. 
Note that the inputs and outputs are in the same format used by SeDuMi. Type

	>> help cdcsOpts
	
for a complete list of solver options.
	
**NOTE:** _this is a research code, and is under active development. You may find 
some undocumented inputs and options that are being used for development 
purposes, in the hope that they will become part of the "official" release. If 
you have any suggestions for improvement, or find any bugs, feel free to [contact us](Contacts)!_


## How to cite<a name="References"></a>

If you find CDCS useful, please cite:

```
@article{ZFPGW2016,
	archivePrefix = {arXiv},
	eprint = {1609.06068v1},
	primaryClass = "math-OC",
	author = {Zheng, Yang and Fantuzzi, Giovanni and Papachristodoulou, Antonis and Goulart, Paul and Wynn, Andrew},
	title = {{Fast ADMM for Semidefinite Programs with Chordal Sparsity}}
	}
	
@misc{CDCS,
    author       = {Zheng, Yang and Fantuzzi, Giovanni and Papachristodoulou, Antonis and Goulart, Paul and Wynn, Andrew},
    title        = {{CDCS}: Cone Decomposition Conic Solver, version 1.0},
    howpublished = {\url{https://github.com/giofantuzzi/CDCS}},
    month        = Sep,
    year         = 2016
}
```

## Contact us<a name="Contacts"></a>
To contact us about ADMM-PDCP, suggest improvements and report bugs, email
* gf910[at]ic.ac.uk (Giovanni Fantuzzi)
* yang.zheng[at]eng.ox.ac.uk	(Yang Zheng)


## Licence<a name="Licence"></a>

CDCS is free software; you can redistribute it and/or modify it under the terms 
of the GNU Lesser General Public Licence (LGPL) as published by the Free Software
Foundation; either version 3 of the Licence, or (at your option) any later version.

CDCS is distributed in the hope that it will be useful, but WITHOUT ANY WARRANTY;
without even the implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR
PURPOSE. See the GNU Lesser General Public License for more details.

You should have received a copy of the GNU Lesser General Public License along 
with this Module; if not, write to the Free Software Foundation, Inc., 
51 Franklin St, Fifth Floor, Boston, MA 02110-1301 USA.
