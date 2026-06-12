---
title: "help in installing ns-2 in ubunthu (are you root?)"
date: 2008-10-27
forum: General Help
---

### Post by junglerat on 2008-10-27
hello 
im trying to install ns-2 and it require perl xgraph 

so im doing : $sudo apt-get install perl xgraph

and i get : 
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

what should i do ? 

this i did once a simple install wont work 

i do :~/NS2/ns-allinone-2.33$ ./install
i get : 
============================================================
* Testing for Darwin (OS X) environment
============================================================
============================================================
* Testing for Cygwin environment
============================================================
Cygwin not detected, proceeding with regular install.
============================================================
* Testing for FreeBSD environment
============================================================
FreeBSD not detected
============================================================
* Build XGraph-12.1
============================================================
cd: 292: can't cd to ./xgraph-12.1
./install: 293: ./configure: not found
make: *** No targets specified and no makefile found.  Stop.
Can not create xgraph; But xgraph is an optional package, continuing...
============================================================
* Build CWeb
============================================================
cd: 312: can't cd to ./cweb
ns-allinone unable to install cweb for you. Please install it manually. cweb is used by sgb to create sgblibrary needed by scenario-generator. But this will not affect the use of ns as such, so continue..
============================================================
* Build Stanford GraphBase
============================================================
cd: 343: can't cd to ./sgb
Unable to create sgb library. This library is used by gt-itm and so for scenario generators. If you already have sgblib (possible if you are on solaris,sunos or freebsd platforms) you may still be able to run gt-itm. so continuing..
============================================================
* Build GT-ITM
============================================================
sgb lib not found. gt-itm & sgb2ns could not be installed. Continuing..
============================================================
* Build zlib
============================================================
cd: 402: can't cd to ./zlib-1.2.3
./install: 414: ./configure: not found
Zlib-1.2.3 configuration failed, but it's optional, so continuing ...
============================================================
* Build tcl8.4.18
============================================================
cd: 424: can't cd to ./tcl8.4.18/unix
/usr/bin/autoconf: 44: cannot create conf5955.sh: Permission denied
/usr/bin/autoconf: 44: cannot create conf5955.sh: Permission denied
chmod: cannot access `conf5955.sh': No such file or directory
autoconf: no input file
./install: 432: ./configure: not found
tcl8.4.18 configuration failed! Exiting ...
Tcl is not part of the ns project.  Please see [www.Scriptics.com](www.Scriptics.com)
to see if they have a fix for your platform.

please help if you can

thank you 
jungle

---

