---
title: "Trust PCI Modem - Intel 536 EP chip, Driver Found, compilation problems"
date: 2005-09-07
forum: Hardware &amp; Laptops
---

### Post by arture on 2005-09-07
Hi, my Trust PCI Modem with Intel 536 EP chip, which i want to use as an Fax, isn't exactly working. Somehow I've got to get some file into /dev/ so that the fax application can address it.

So I've startet searching and lukily i found drivers on 

[http://downloadfinder.intel.com/scripts-df-external/filter_results.aspx?strTypes=all&ProductID=977&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go%21](http://downloadfinder.intel.com/scripts-df-external/filter_results.aspx?strTypes=all&ProductID=977&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go%21)

which i just seem to have to compile.

So following the readme I've unpacked into the directory given changed to there 
typed "make clean" 
and typed "make 536
"

That was were the problems startet. I installed the Kernel headers for my kernel, i installed gcc and the build-essentials (some advices were given) but still i had some problems with a directory named vmlinuz which don't seem to have.

So i don't really know what to do... I've already copied autoconf.h into the directory from somewhere else, /boot/vmlinuz.autoconf.h and with /boot/vmlinuz.version.h I'm stuck.

I've tried make config_sync but it just said it misses version.h.

So if anybody can help, I'd really apreciate.


The last Step would be:


   6. Type: make install

This will create a /dev/modem device file. This file is used as an interface to 

modem by all applications: minicom, kpppd, efax, etc. Please configure the applications

to use /dev/modem if neccessary.


This is where i'd like to be*g*

---

