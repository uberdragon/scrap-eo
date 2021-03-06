# scrap-eo
CLI for scraping data from webpages for SEO analysis

## Installation
It is recommended that you have the *virtualenv* Python package installed so scrap-eo can install it's required packages in an isolated environment without risk of creating conflicts with existing Python packages already installed on your system.

`pip install virtualenv`

You may have to run the above command as root.
With virtualenv installed on your system, you can follow the recommended steps below to install scrap-eo in its own isolated environment:

* clone the scrap-eo repo
* `mkdir -p ~/.virtualenvs`
* `virtualenv ~/.virtualenvs/scrapeo`
* `source ~/.virtualenvs/scrapeo/bin/activate`
* `cd` into the cloned repo
* `pip install --editable .`
* `deactivate`

After running `pip install .`, an executable Python file will be generated in your *.virtualenvs/scrapeo/bin* directory called *scrapeo*. It is useful to create a symbolic link to this file in a directory that is listed for your path. For example `ln -s /home/<user>/.virtualenvs/scrapeo/bin/scrapeo /usr/local/bin/scrapeo` will allow you to run scrapeo from anywhere without having to type the full path to the executable (if */usr/local/bin/* is listed in your path environment variable).

## Planned Features
* ~~Create an API for scrap-eo, moving the functions for scraping data to a separate file that contains a `ScrapEO` class~~
* ~~Add an argument to the `--meta` option to scrape the content from all meta tags in a document (e.g. `--meta *`)~~
* Deal with and provide information about non-self-closing meta tags
* Add regex matching functionality to the `--meta` option
* Add option to audit sites making use of HTML5 spec 
* ~~Add colored output support ([colorama](https://pypi.python.org/pypi/colorama) integration with click)~~
* Setup a Makefile for easier installation
* Move all existing options to their own commands (i.e., `scrapeo meta http://example.com` and `scrapeo title http://example.com`)
* Add an option to read multiple URL's from a single file
* Search case insensitively for the name / property / http-equiv attribute specified by the `--meta` option

## Version Notes
### 1.1
* Very simple API for the basic scrap-eo functions (found in *scrapeo/core.py*)
* Provide multiple arguments to find meta tags by name using multiple instances of the `--meta` option
* Connection errors now provide more human-readable information
* Bugfix for URL's with UTF-8 encoded characters

#### 1.1.2
* Added the --allmeta option to get the content from every self-closing meta tag in the document
* Made output from meta commands more readable by using indentation 
* Added ANSI colors to output
* `--articles` option prints information about content encapsualted by the HTML5 `article` sectioning element
* Improved how meta tags are searched for with the `--allmeta` option so that more meaningful data is returned
