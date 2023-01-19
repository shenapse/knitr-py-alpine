

# A docker image to knit Rmd files

A alpine-based docker image with

- R version 4.2.2 (2022-10-31) (with renv, knitr and reticulate)
- Python 3.9.16
- Poetry (version 1.3.2)

The image might be useful to include output of codes in README.md. Indeed, this README.md is generated by `knitr::knit`ing README.rmd.

(For Docker Hub) This image is maintained at

```
https://github.com/Shena4746/knitr-py-alpine
```

## Usage

The following command knits README.rmd at your project top to produce README.md.

```
docker run -it --rm -v ${PWD}:/root/workdir shena4746/knitr-py-alpine:0.0.1 Rscript -e "knitr::knit('README.rmd')"
```

## Install

The images is available at Docker hub.


```
docker pull shena4746/knitr-py-alpine:0.0.1
```

## Customise/Exntend

You can change version of R/python by specifying values in `./.env`, and then `make build`. The specified python version should be available by the latest pyenv. To install new packages, renv and poetry would be useful.

## Version info


```sh
cat /etc/os-release;
cat /proc/version
```

```
NAME="Alpine Linux"
ID=alpine
VERSION_ID=3.17.1
PRETTY_NAME="Alpine Linux v3.17"
HOME_URL="https://alpinelinux.org/"
BUG_REPORT_URL="https://gitlab.alpinelinux.org/alpine/aports/-/issues"
Linux version 5.15.79.1-microsoft-standard-WSL2 (oe-user@oe-host) (x86_64-msft-linux-gcc (GCC) 9.3.0, GNU ld (GNU Binutils) 2.34.0.20200220) #1 SMP Wed Nov 23 01:01:46 UTC 2022
```



```r
R.version
```

```
               _                           
platform       x86_64-pc-linux-musl        
arch           x86_64                      
os             linux-musl                  
system         x86_64, linux-musl          
status                                     
major          4                           
minor          2.2                         
year           2022                        
month          10                          
day            31                          
svn rev        83211                       
language       R                           
version.string R version 4.2.2 (2022-10-31)
nickname       Innocent and Trusting       
```

```r
# R packages
library(magrittr)
installed.packages() %>%
    as.data.frame() %>%
    .[, c("Package", "Version")]
```

```
              Package Version
Matrix         Matrix   1.5-3
Rcpp             Rcpp   1.0.9
RcppTOML     RcppTOML   0.2.0
base             base   4.2.2
cli               cli   3.6.0
compiler     compiler   4.2.2
datasets     datasets   4.2.2
evaluate     evaluate    0.20
glue             glue   1.6.2
grDevices   grDevices   4.2.2
graphics     graphics   4.2.2
grid             grid   4.2.2
here             here   1.0.1
highr           highr    0.10
jsonlite     jsonlite   1.8.4
knitr           knitr    1.41
lattice       lattice 0.20-45
lifecycle   lifecycle   1.0.3
magrittr     magrittr   2.0.3
methods       methods   4.2.2
parallel     parallel   4.2.2
png               png   0.1-8
rappdirs     rappdirs   0.3.3
renv             renv  0.16.0
reticulate reticulate    1.27
rlang           rlang   1.0.6
rprojroot   rprojroot   2.0.3
splines       splines   4.2.2
stats           stats   4.2.2
stats4         stats4   4.2.2
stringi       stringi  1.7.12
stringr       stringr   1.5.0
tcltk           tcltk   4.2.2
tools           tools   4.2.2
utils           utils   4.2.2
vctrs           vctrs   0.5.1
withr           withr   2.5.0
xfun             xfun    0.36
yaml             yaml   2.3.6
```


```sh
python --version;
pip list
```

```
Python 3.9.16
Package    Version
---------- -------
pip        22.0.4
setuptools 58.1.0
wheel      0.38.4
WARNING: You are using pip version 22.0.4; however, version 22.3.1 is available.
You should consider upgrading via the '/usr/local/bin/python -m pip install --upgrade pip' command.
```
