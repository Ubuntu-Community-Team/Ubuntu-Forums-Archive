---
title: "configuring a package"
date: 2009-01-28
forum: Installation &amp; Upgrades
---

### Post by rpete on 2009-01-28
Hi, I am trying to install mdbtools in order to view a database I created using MS Access.  I do not have a partition, but only has Ubuntu as my operating system, version 8.04.  When I attempt to install mdbtools I get the output below.  I need to configure two packages it seems.  They are in the repository and the box is grayed in in synaptic package manager.  Could anyone walk me through the steps to correctly configure these packages?  I realize I made a typo error on one attempt to use <sudo dpkg -r libghc6-hsql-postgresql-dev> but I don't understand the final error <database area is locked by another process>

dpkg: error processing libghc6-hsql-postgresql-dev (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of libghc6-hsql-postgresql-prof:
 libghc6-hsql-postgresql-prof depends on libghc6-hsql-postgresql-dev (= 1.7-1); however:
  Package libghc6-hsql-postgresql-dev is not configured yet.
dpkg: error processing libghc6-hsql-postgresql-prof (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libghc6-hsql-postgresql-dev
 libghc6-hsql-postgresql-prof
E: Sub-process /usr/bin/dpkg returned an error code (1)
richard@dell-desktop:~$ sudo dpkig -r libghc6-hsql-postgresql-dev
[sudo] password for richard: 
sudo: dpkig: command not found
richard@dell-desktop:~$ sudo dpdg -r libghc6-hsql-postgresql-dev
sudo: dpdg: command not found
richard@dell-desktop:~$ sudo dpkg -r libghc6-hsql-postgresql-dev
dpkg: status database area is locked by another process
richard@dell-desktop:~$

---

### Post by avtolle on 2009-01-28
Is Synaptic still open? If so, close it, then run the final command again. If it successfully removes the package, then open Synaptic again for the purpose of installing the needed packages.

---

### Post by rpete on 2009-01-28
Hi, I removed the ....prof package then reinstalled it through synaptic manager but I had a problem with the ....libghc6-hsql-postgresql-dev package.  I got the message that there was a dependency problem so I couldn't remove it.  What should I try next?

---

### Post by rpete on 2009-01-28
I thought I had it figured out when I tried the command <sudo apt-get build-dep libghc6-hsql-postgresql-dev> There is still a configure problem as you can see in the terminal output.  Any ideas?

richard@dell-desktop:~$ sudo apt-get build-dep libghc6-hsql-postgresql-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  cpphs dpatch ghc6-doc ghc6-prof haddock haskell-devscripts
0 upgraded, 6 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 12.3MB of archives.
After this operation, 94.3MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe cpphs 0.7-4 [211kB]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main dpatch 2.0.28 [87.1kB]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe haddock 0.8-2 [528kB]
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe ghc6-doc 6.8.2-2ubuntu1 [2414kB]
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe ghc6-prof 6.8.2-2ubuntu1 [9078kB]
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe haskell-devscripts 0.6.7 [17.8kB]
Fetched 12.3MB in 35s (348kB/s)                                                
Selecting previously deselected package cpphs.
(Reading database ... 327099 files and directories currently installed.)
Unpacking cpphs (from .../archives/cpphs_0.7-4_i386.deb) ...
Selecting previously deselected package dpatch.
Unpacking dpatch (from .../archives/dpatch_2.0.28_all.deb) ...
Selecting previously deselected package haddock.
Unpacking haddock (from .../haddock_0.8-2_i386.deb) ...
Selecting previously deselected package ghc6-doc.
Unpacking ghc6-doc (from .../ghc6-doc_6.8.2-2ubuntu1_all.deb) ...
Selecting previously deselected package ghc6-prof.
Unpacking ghc6-prof (from .../ghc6-prof_6.8.2-2ubuntu1_i386.deb) ...
Selecting previously deselected package haskell-devscripts.
Unpacking haskell-devscripts (from .../haskell-devscripts_0.6.7_all.deb) ...
Setting up libghc6-hsql-postgresql-dev (1.7-1) ...
Reading package info from "/usr/lib/haskell-packages/ghc6/lib/hsql-postgresql-1.7/installed-pkg-config" ... done.
ghc-pkg: /usr/include/postgresql/8.3/server doesn't exist or isn't a directory (use --force to override)
dpkg: error processing libghc6-hsql-postgresql-dev (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of libghc6-hsql-postgresql-prof:
 libghc6-hsql-postgresql-prof depends on libghc6-hsql-postgresql-dev (= 1.7-1); however:
  Package libghc6-hsql-postgresql-dev is not configured yet.
dpkg: error processing libghc6-hsql-postgresql-prof (--configure):
 dependency problems - leaving unconfigured
Setting up cpphs (0.7-4) ...
Setting up dpatch (2.0.28) ...
Setting up haddock (0.8-2) ...

Setting up ghc6-doc (6.8.2-2ubuntu1) ...

Setting up ghc6-prof (6.8.2-2ubuntu1) ...
Setting up haskell-devscripts (0.6.7) ...
Errors were encountered while processing:
 libghc6-hsql-postgresql-dev
 libghc6-hsql-postgresql-prof
E: Sub-process /usr/bin/dpkg returned an error code (1)
E: Failed to process build dependencies
richard@dell-desktop:~$

---

