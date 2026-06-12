---
title: "WifiScanner 1.0.1"
date: 2009-11-12
forum: Installation &amp; Upgrades
---

### Post by jtapiaFE on 2009-11-12
I am trying to install WifiScanner 1.0.1 on my ubuntu system I get an error has someone seen this error before?

root@variant:/home/johnta/Desktop/WifiScanner-1.0.1# ./autogen.sh
Prototype mismatch: sub Automake::SEEK_SET: none vs () at /usr/share/perl/5.10/Exporter.pm line 66.
 at /usr/local/bin/automake line 8348
Prototype mismatch: sub Automake::SEEK_CUR: none vs () at /usr/share/perl/5.10/Exporter.pm line 66.
 at /usr/local/bin/automake line 8348
Prototype mismatch: sub Automake::SEEK_END: none vs () at /usr/share/perl/5.10/Exporter.pm line 66.
 at /usr/local/bin/automake line 8348
processing .
aclocal
aclocal: configure.in: 12: macro `AM_DISABLE_SHARED' not found in library
aclocal: configure.in: 13: macro `AM_ENABLE_STATIC' not found in library
aclocal: configure.in: 339: macro `AM_PATH_GLIB_2_0' not found in library

this is when I run autogen?

---

