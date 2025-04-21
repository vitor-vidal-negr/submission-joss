![pyRDDSP](https://github.com/user-attachments/assets/28382bd4-0f4c-42e7-b06d-bf235ce90433)---
title: 'pyRDDSP - A python package implementation of RDDSP-SAEA algorithm application'
tags:
  - principal component analysis
  - partial least squares regression
  - evolutionary optimization
  - surrogate assisted optimization
  - Docker
authors:
 - name: Vitor Vidal de Negreiros
   orcid: 0009-0009-1677-2105
   affiliation: 1
 - name: Lucas Souza Batista
   orcid: 0000-0002-7444-3440
   affiliation: 2
affiliations:
 - name: Graduate Program in Electrical Engineering, Universidade Federal de Minas Gerais, Brazil
   index: 1
 - name: Departament of Electrical Engineering, Universidade Federal de Minas Gerais, Brazil
   index: 2
 - name: Operations Research and Complex Systems Laboratory, Universidade Federal de Minas Gerais, Brazil
   index: 3
date: 25 april 2025
bibliography: paper.bib
---

# Summary

Traditional Evolutionary Algorithms (EAs) and Surrogate Assisted Evolutionary Algorithms (SAEAs) have been applied successfully to a wide range of optimization problems. However, in the context of expensive optimization, the computational budget is highly limited. The reduced number of fitness evaluations available in this scenario represents a great challenge for EAs and SAEAs. Even the special class of so-called large-scale algorithms [1–3], particularly designed for high-dimensional data, not always yield good results due to the limited number of fitness evaluations available.

Expensive problems can take several hours to compute a single cost function execution and require specific hardware and design capabilities. Examples of such challenges include aircraft wing shape optimization [4], vehicle crash safety design [5, 6], meteorological simulations [7, 8], and Finite Element Analysis (FEM) problems [9], where evolutionary optimization is particularly difficult due to the high computational cost.

pyRDDSP package is an implementation of RDDSP-SAEA, a surrogate assisted evolutionary algorithm for high-dimensional expensive problems. RDDSP-SAEA is based on DSP-SAEA [] and evolved the global-local search approach by incorporating the so-called Enhanced Surrogate Pool (ESP) for local search and Multi-Decision Space Partitioning (MDSP) for global search. RDDSP-SAEA integrates Principal Component Analysis (PCA) and Partial Least Squares (PLS) regression in a combined dimension-reduction strategy to address the challenge of building surrogate models with a very limited number of samples. 

RDDSP-SAEA implemented in pyRDDSP follows the design of global-local search. This algorithm structure is composed of two main parts [10]: 1) global-search - resposible for exploration and usually based on surrogate models trained in the global search space. 2) Local search stage - responsible for exploitation and usually based on surrogate models trained in restricted regions of the search space.

In addition to the RDSSP-SAEA algorthm it-self, pyRDDSP also brings CEC2005 [] test problems suite integrated in the package. The CEC2005 class from pyRDSSP allows users to easily instantiate and use CEC2005 test problems. This test suite is highly used by the optimization community and the implementation provided in pyRDDSP expands the original test suite to include test data for 300, 500 and 700 variables, while the original implementation has a limit of 100 variables. 

In pyRDDSP, global search is based on the MDSP strategy and local search is based on ESP strategy. Both phases rely on PCA an PLS dimension reduction techniques to produce multiple lower-dimensional spaces and surrogates trained with a reduced number of variables. Making it possible to have good surrogate models even for expensive high-dimensional data sets. The main contrbutions of RDDSP algorithm and pyRDDSP package are:

- Introduction of RDDSP-SAEA, a competitive surrogate assisted algorithm for expensive high-dimensional problems.
- Integrated CEC2005 test suite for experiments analysis and design.
- MDSP - Multi-Decision Space Partitioning approach for global search. A strategy where multiple lower dimensional spaces are clustered and partitoned. RBF surrogates are trained for each of the cluster regions accroos the multiple decision spaces, and only the decision space that yields the best surrogates is selected to be used for further optimization.
- ESP strategy for local search. Multiple surrogate modelining techniques are applied (RBF, Kriging, Polynomial Regression and surrogate Ensembles) and trained on both the original decision space and lower-dimensional spaces produced by a combined form of PCA/PLS techniques. PLS and PCA are used together so way the algorithm can select the projections that yield the best models.

![img/pyRDDSP_structure.png](img/pyRDDSP_structure.png)

# Statement of need


# Acknowledgements

The authors would like to thank all the reviewers for their constructive comments. This work was supported by Brazilian agencies FAPEMIG (Research Support Foundation of the State of Minas Gerais), CNPq (The National Council for Scientific and Technological Development), CAPES (Coordination for the Improvement of Higher Education Personnel), and the Operations Research and Complex Systems Laboratory (ORCS Lab./UFMG)\footnote{https://orcslab.github.io/}. Professor Lucas S. Batista is a FAPEMIG-CNPQ scholarship holder (process APQ-06716-24).

# References
