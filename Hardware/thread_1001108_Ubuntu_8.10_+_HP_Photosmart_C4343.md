---
title: "Ubuntu 8.10 + HP Photosmart C4343"
date: 2008-12-03
forum: Hardware
---

### Post by Elkaz on 2008-12-03
Hello all.
I am from Russia, so sorry for my english. And I am newbie Ubuntu user :-[
I am asking you for your help, because no one on russian ubuntu forums can help me. So, what's a problem.
I bought a new all-in-one (Printer, Scanner, Copier, Fax) HP Photosmart C4343. I downloaded drivers from HP official website (it redirects somewhere, I don't remember now where exactly). I instelled drivers. 
Now, I wanted to check it. I got into openoffice and tryed to print document. But I got only 3-4 strings (from the beginning) of the whole document... 

Can some one help in my problem?

P.s
All programs print like this, not only openoffice. So, I think, that problems in drivers.

Thanks a lot

---

### Post by jheaton5 on 2008-12-03
Included in 8.10 is an HP print/fax/scanner management software package called HPLIP.  I installed this with synaptic package manager and was able to set up my HP Photosmart Printer which is on my wireless network.  My printer is model C8180.

---

### Post by Elkaz on 2008-12-03
Thanks for answer.
But I still had this problem. Installed HPLIP (with Synaptic). Now he prints nearly 60-85% of the text.

---

### Post by Elkaz on 2008-12-04
Up... Please, someone, help =) Question of life and death

---

### Post by 11hjpphty76lkjj on 2008-12-04
Please run hp-check -t and post the output.

Aaron

---

### Post by Elkaz on 2008-12-05
elkaz@elkaz-laptop:~$ hp-check -t

HP Linux Imaging and Printing System (ver. 2.8.7)
Dependency/Version Check Utility ver. 14.0

Copyright (c) 2001-8 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

Note: hp-check can be run in three modes:
1. Compile-time check mode (-c or --compile): Use this mode before compiling the
HPLIP supplied tarball (.tar.gz or .run) to determine if the proper dependencies
are installed to successfully compile HPLIP.                                    
2. Run-time check mode (-r or --run): Use this mode to determine if a distro    
supplied package (.deb, .rpm, etc) or an already built HPLIP supplied tarball   
has the proper dependencies installed to successfully run.                      
3. Both compile- and run-time check mode (-b or --both) (Default): This mode    
will check both of the above cases (both compile- and run-time dependencies).   

Saving output in log file: hp-check.log

Initializing. Please wait...
warning: Invalid ppd_dir value: None

---------------
| SYSTEM INFO |
---------------

Basic system information:
Linux elkaz-laptop 2.6.27-9-generic #1 SMP Thu Nov 20 21:57:00 UTC 2008 i686 GNU/Linux

Distribution:
ubuntu 8.10

HPOJ running?
No, HPOJ is not running (OK).

Checking Python version...
OK, version 2.5.2 installed

Checking PyQt version...
OK, version 3.17 installed.

Checking SIP version...
error: SIP not installed or version not found.

Checking for CUPS...
Status: &#1087;&#1083;&#1072;&#1085;&#1080;&#1088;&#1086;&#1074;&#1097;&#1080;&#1082; &#1079;&#1072;&#1087;&#1091;&#1097;&#1077;&#1085;
Version: 1.3.9
error_log is set to level: warn
note: For troubleshooting printing issues, it is best to have the CUPS 'LogLevel'
note: set to 'debug'. To set the LogLevel to debug, edit the file /etc/cups/cupsd.conf (as root),
note: and change the line near the top of the file that begins with 'LogLevel' to read:
note: LogLevel debug
note: Save the file and then restart CUPS (see your OS/distro docs on how to restart CUPS).
note: Now, when you print, helpful debug information will be saved to the file:
note: /var/log/cups/error_log
note: You can monitor this file by running this command in a console/shell:
note: tail -f /var/log/cups/error_log

Checking for dbus/python-dbus...
dbus daemon is running.
python-dbus version: 0.82.4


------------------------------------
| COMPILE AND RUNTIME DEPENDENCIES |
------------------------------------

note: To check for compile-time only dependencies, re-run hp-check with the -c parameter (ie, hp-check -c).
note: To check for run-time only dependencies, re-run hp-check with the -r parameter (ie, hp-check -r).

Checking for dependency: cups - Common Unix Printing System...
OK, found.

Checking for dependency: cups-ddk - CUPS driver development kit...
OK, found.

Checking for dependency: cups-devel- Common Unix Printing System development files...
OK, found.

Checking for dependency: dbus - Message bus system...
OK, found.

Checking for dependency: gcc - GNU Project C and C++ Compiler...
OK, found.

Checking for dependency: GhostScript - PostScript and PDF language interpreter and previewer...
OK, found.

Checking for dependency: libcrypto - OpenSSL cryptographic library...
OK, found.

Checking for dependency: libjpeg - JPEG library...
OK, found.

Checking for dependency: libnetsnmp-devel - SNMP networking library development files...
OK, found.

Checking for dependency: libpthread - POSIX threads library...
OK, found.

Checking for dependency: libtool - Library building support services...
OK, found.

Checking for dependency: libusb - USB library...
OK, found.

Checking for dependency: make - GNU make utility to maintain groups of programs...
OK, found.

Checking for dependency: PIL - Python Imaging Library (required for commandline scanning with hp-scan)...
OK, found.

Checking for dependency: ppdev - Parallel port support kernel module....
OK, found.

Checking for dependency: PyQt - Qt interface for Python...
OK, found.

Checking for dependency: python-ctypes - A foreign function library for Python...
OK, found.

Checking for dependency: python-dbus - Python bindings for dbus...
OK, found.

Checking for dependency: python-devel - Python development files...
OK, found.

Checking for dependency: Python 2.3 or greater - Required for fax functionality...
OK, found.

Checking for dependency: Python 2.2 or greater - Python programming language...
OK, found.

Checking for dependency: Reportlab - PDF library for Python...
OK, found.

Checking for dependency: SANE - Scanning library...
OK, found.

Checking for dependency: SANE - Scanning library development files...
OK, found.

Checking for dependency: scanimage - Shell scanning program...
OK, found.

Checking for dependency: xsane - Graphical scanner frontend for SANE...
OK, found.


----------------------
| HPLIP INSTALLATION |
----------------------


Currently installed HPLIP version...
HPLIP 2.8.7 currently installed in '/usr/share/hplip'.

Current contents of '/etc/hp/hplip.conf' file:
# hplip.conf.  Generated from hplip.conf.in by configure.

[hplip]
version=2.8.7

[dirs]
home=/usr/share/hplip
run=/var/run
ppd=/usr/share/ppd/hpijs/HP
ppdbase=/usr/share/ppd/hpijs
doc=/usr/share/doc/hplip-doc/HTML
icon=no
cupsbackend=/usr/lib/cups/backend
cupsfilter=/usr/lib/cups/filter
drv=/usr/share/cups/drv

# Following values are determined at configure time and cannot be changed.
[configure]
network-build=yes
pp-build=yes
gui-build=yes
scanner-build=yes
fax-build=yes
dbus-build=yes
cups11-build=no
doc-build=yes
shadow-build=no
foomatic-drv-install=yes
foomatic-ppd-install=no
foomatic-rip-hplip-install=no
internal-tag=2.8.7.3
restricted-build=no



-------------------------------
| DISCOVERED PARALLEL DEVICES |
-------------------------------

No devices found.

--------------------------
| DISCOVERED USB DEVICES |
--------------------------

No devices found.

---------------------------------
| INSTALLED CUPS PRINTER QUEUES |
---------------------------------

 
warning: No queues found.

----------------------
| SANE CONFIGURATION |
----------------------

'hpaio' in '/etc/sane.d/dll.conf'...
OK, found. SANE backend 'hpaio' is properly set up.

Checking output of 'scanimage -L'...
 
No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).


---------------------
| PYTHON EXTENSIONS |
---------------------

Checking 'cupsext' CUPS extension...
OK, found.

Checking 'pcardext' Photocard extension...
OK, found.

Checking 'hpmudext' I/O extension...
OK, found.

Checking 'scanext' SANE scanning extension...
OK, found.


-----------------
| USB I/O SETUP |
-----------------


Checking for permissions of USB attached printers...
 
-----------
| SUMMARY |
-----------

error: 1 error or warning.

Please refer to the installation instructions at:
[http://hplip.sourceforge.net/install/index.html](http://hplip.sourceforge.net/install/index.html)


Done.
elkaz@elkaz-laptop:~$

---

### Post by Elkaz on 2008-12-05
Is it give something?

---

### Post by Elkaz on 2008-12-05
I get into HPLIP -> actions -> print test page. It just "ate" my paper and give it back. Without any text on it

---

### Post by Elkaz on 2008-12-05
Up

---

### Post by 11hjpphty76lkjj on 2008-12-07
The hp-check doesn't seem to show any printer queues.

Try running:
```

sudo apt-get update
sudo apt-get install hplip-gui
```

then then:
```

sudo hp-setup
```

---

### Post by Elkaz on 2008-12-07
Thanks. Seems, that this worked)
Topic can be closed

---

