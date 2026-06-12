---
title: "packages listed without Section or Priority"
date: 2009-10-02
forum: Installation &amp; Upgrades
---

### Post by ermeyers on 2009-10-02
I've been experimenting with apt-get install/purge of packages and metapackages, and I've written some perl programs using Apt::Cache from the package libapt-pkg-perl to discover the underlying package Depends, Recommends, Suggests, etc..  A simple program call of 'apt-cache pkgnames | sort > apt_cache_pkgnames.txt' gives a list of 34809 available package names, and I wrote an Apt::Cache based program that prints out the Section and Priority fields for these packages, and I found 7968 of the 34809 packages listed didn't have a Section or Priority defined.

The first of the packages listed is 3c5x9utils, and 'apt-get -s install 3c5x9utils' says that package nictools-nopci replaces it.  Okay, fine, it's replaced by another package.

The second of the packages listed is 7z, and 'apt-get -s install 7z' says the following:[INDENT]# apt-get -s install 7z
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package 7z is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package 7z has no installation candidate
[/INDENT][INDENT]# apt-cache rdepends 7z
<7z>
# apt-cache depends 7z
<7z>
[/INDENT]Please explain this 7z type of situation, in which: "E: Package ... has no installation candidate"

Why are they listed, and where on Ubuntu or Debian sites is there a web page describing the logic of void packages.

---

