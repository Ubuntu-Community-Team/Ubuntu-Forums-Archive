---
title: "Fama on Ubuntu 9.04"
date: 2009-07-06
forum: Installation &amp; Upgrades
---

### Post by phoenix910 on 2009-07-06
Hi there, I'm attempting to build Fama on Ubuntu Server 9.04, and I ran ./configure with the following results:

root@ovz-test:~/fama-0.0.3# ./configure 
Checking for Python                     :  033[92m/usr/bin/python033[0m
Checking for WAF                        :  033[92m/root/fama-0.0.3/waf033[0m
calling waf configure with parameters
/root/fama-0.0.3/.waf-1.1.1-1347319704/wafadmin/Params.py:7: DeprecationWarning: the md5 module is deprecated; use hashlib instead
  import os, sys, types, inspect, md5, base64, stat
Checking for program gcc                : ok /usr/bin/gcc 
Checking for program ar                 : ok /usr/bin/ar 
Checking for program ranlib             : ok /usr/bin/ranlib 
Checking for program cpp                : ok /usr/bin/cpp 
Checking for compiler could create pragramms : ok  
Checking for compiler could create shared libs : ok  
Checking for compiler could create static libs : ok  
Checking for flags -Wall                       : ok  
Checking for flags -O2                         : ok  
Checking for flags -g -DDEBUG                  : ok  
Checking for flags -g3 -O0 -DDEBUG             : ok  
Checking for gcc                               : ok  
Checking for package glib-2.0 >= 2.10.0 (cached)  : not found 
Checking for package libtapioca-client-glib-0.14 >= 0.14.0.2 (cached)  : not found 
Checking for package gobject-2.0 >= 2.10.0 (cached)                    : not found 
Checking for header ncursesw/panel.h (cached)                          : not found 
Checking for header ncursesw/ncurses.h (cached)                        : not found 



Now, I know for a fact that I have glib, etc installed, yet it is "not found". I was wondering if the (cached) had anything to do with it? I hope someone can help, as there are no i386 binary builds for Jaunty yet, and none of the others work, seemingly, on it. Thanks,

~phoenix910

---

