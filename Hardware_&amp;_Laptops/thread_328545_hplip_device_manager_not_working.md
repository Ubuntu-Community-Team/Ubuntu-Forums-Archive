---
title: "hplip device manager not working"
date: 2006-12-31
forum: Hardware &amp; Laptops
---

### Post by eilu on 2006-12-31
Just noticed it today, but the HP device manager ($ hplip-toolbox) is not working; neither are the other hp tools (I've tried $ hp-levels; $ hp-info etc.)

on terminal, this is what happens (sorry about the looooong post):
```
**$ hp-toolbox**

HP Linux Imaging and Printing System (ver. x.x.x)
HP Device Manager ver. 6.3

Copyright (c) 2003-6 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

error: Unable to connect to HPLIP I/O. Check and make sure HPLIP is running.
error: Unable to create client object.
[B]
$ hp-check[/B]

HP Linux Imaging and Printing System (ver. x.x.x)
Dependency/Version Check Utility ver. 4.0

Copyright (c) 2003-6 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

---------------
| SYSTEM INFO |
---------------
Basic system info (uname -a):
  --> Linux cerebrum 2.6.15-27-386 #1 PREEMPT Fri Dec 8 17:51:56 UTC 2006 i686 GNU/Linux
Detected distro (/etc/issue):
  --> ubuntu 6.06
Detected distro (lsb_release):
   --> Ubuntu 6.06 (dapper)
Currently installed version...
  --> OK, not found.
HPLIP running?
   --> No, HPLIP is not running (OK).
HPOJ running?
   --> No, HPOJ is not running (OK).
Checking Python version...
  --> OK, version 2.4.3 installed

----------------
| DEPENDENCIES |
----------------
Checking for dependency 'libcrypto (libcrypto - OpenSSL cryptographic library)'...
  --> OK, found.
Checking for dependency 'gcc (gcc - GNU Project C and C++ Compiler)'...
  --> OK, found.
Checking for dependency 'sane (SANE - Scanning library)'...
  --> OK, found.
Checking for dependency 'gs (GhostScript - PostScript and PDF language interpreter and previewer)'...
  --> OK, found.
Checking for dependency 'libjpeg (libjpeg - JPEG library)'...
  --> OK, found.
Checking for dependency 'libpthread (libpthread - POSIX threads library)'...
  --> OK, found.
Checking for dependency 'make (make - GNU make utility to maintain groups of programs)'...
  --> OK, found.
Checking for dependency 'python-devel (python-devel - Python development files)'...
  --> OK, found.
Checking for dependency 'reportlab (Reportlab - PDF library for Python)'...
  --> OK, found.
Checking for dependency 'pyqt (PyQt - Qt interface for Python)'...
  --> OK, found.
Checking for dependency 'cups-devel (cups-devel- Common Unix Printing System development files)'...
  --> OK, found.
Checking for dependency 'ppdev (ppdev - Parallel port support kernel module.)'...
  --> OK, found.
Checking for dependency 'libusb (libusb - USB library)'...
  --> OK, found.
Checking for dependency 'scanimage (scanimage - Shell scanning program)'...
  --> OK, found.
Checking for dependency 'libnetsnmp-devel (libnetsnmp-devel - SNMP networking library development files)'...
  --> OK, found.
Checking for dependency 'python2x (Python 2.2 or greater - Python programming language)'...
  --> OK, found.
Checking for dependency 'lsb (LSB - Linux Standard Base support)'...
  --> OK, found.
Checking for dependency 'xsane (xsane - Graphical scanner frontend for SANE)'... 
  error:   Not found!
This is an OPTIONAL dependency.
Checking for dependency 'cups (cups - Common Unix Printing System)'...
  --> OK, found.
Checking for dependency 'python23 (Python 2.3 or greater - Required for fax functionality)'...
  --> OK, found.

----------------------
| INSTALLED PRINTERS |
----------------------
Deskjet_D2300
-------------
Device URI: usb://HP/Deskjet%20D2300%20series?serial=TH6AO150ZJ04KT
Installed in HPLIP? No
PPD: /etc/cups/ppd/Deskjet_D2300.ppd
PPD Description: HP DeskJet D2300 Foomatic/hpijs (recommended)

Printer status:
printer Deskjet_D2300 is idle.  enabled since Friday, 29 December, 2006 06:32:59 PM PHT

Traceback (most recent call last):
  File "/usr/bin/hp-check", line 285, in ?
    if back_end == 'hpfax' and desc != 'HP Fax':
NameError: name 'back_end' is not defined

**$ hp-levels**

HP Linux Imaging and Printing System (ver. x.x.x)
Supply Levels Utility ver. 1.0

Copyright (c) 2003-6 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

error: Error occured during interactive mode. Exiting.

**$ hp-info**

HP Linux Imaging and Printing System (ver. x.x.x)
Device Information Utility ver. 3.4

Copyright (c) 2003-6 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

error: Error occured during interactive mode. Exiting.
```


I can still print alright, test pages come out okay (it spits out the Ubuntu test page which has the Ubuntu logo, some lines and strips of color, not HP's test page, which is a picture of some fruit), hardware buttons work, etc. CUPS lists the printer's driver as "hpijs". It's just the more advanced features (eg., alignment, cartridge level monitoring, cleaning) missing. Any ideas? Should I try reinstalling? I manually installed the latest version (v1.6.10) using the installer provided on the hplip website so it's not listed in Synaptic.

Recent system changes: I cleared out some residual config files in Synaptic and did a sudo apt-get autoclean.

Thanks.

---

### Post by 11hjpphty76lkjj on 2007-01-12
What happens if you run 

sudo /etc/init.d/hplip restart

and then hp-toolbox

A

---

### Post by eilu on 2007-01-30
actually I went for reinstalling it from scratch. It works now. No idea what happened the last time though. must be gremlins! :D Thanks anyway.

---

### Post by gorg on 2007-02-02
i went to the toolbox site to add a printer . how do i register for the site. i get as afar as user and password but it won't accept anything i punch in.
thanks

---

### Post by 11hjpphty76lkjj on 2007-02-03
```
i went to the toolbox site to add a printer . how do i register for the site. i get as afar as user and password but it won't accept anything i punch in.
thanks
```

Sorry I'm not sure what site you are talking about.  What's the url?

A

---

### Post by w6kkt on 2007-02-03
1.  HP toolbox needs  Python-qt3 package to operate.  Use synaptic to install pythonQT3.

2.  go into /usr/share/applications and look for the HPLIP or HP toolbox icon.  Using your mouse, copy it to your desktop.  Dbl click icon and toolbox should work with your HP printer.

---

