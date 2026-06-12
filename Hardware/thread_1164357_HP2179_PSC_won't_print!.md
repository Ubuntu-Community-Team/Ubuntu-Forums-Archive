---
title: "HP2179 PSC won't print!"
date: 2009-05-19
forum: Hardware
---

### Post by drifter129 on 2009-05-19
i have recently installed ubuntu 9.04 and cannot seem to get my HP 2179 printer working.

linux detects the printer ok - i have downloaded the HPLIP drivers from synaptic, but whenever i send a job - nothing happens. the jobs just sit in the queue saying "pending".

Any ideas?

---

### Post by 11hjpphty76lkjj on 2009-05-25
Run
```

hp-check -t
```

and post the output.

---

### Post by drifter129 on 2009-05-27
HP Linux Imaging and Printing System (ver. 3.9.2)
Dependency/Version Check Utility ver. 14.1

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
 
---------------
| SYSTEM INFO |
---------------

Basic system information:
Linux ed-desktop 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686 GNU/Linux

Distribution:
ubuntu 9.04

HPOJ running?
No, HPOJ is not running (OK).

Checking Python version...
OK, version 2.6.2 installed

Checking PyQt 4.x version...
OK, version 4.4.4 installed.

Checking for CUPS...
Status: scheduler is running
error: Version: (Not available. CUPS may not be installed or not running.)

Checking for dbus/python-dbus...
dbus daemon is running.
python-dbus version: 0.83.0


------------------------------------
| COMPILE AND RUNTIME DEPENDENCIES |
------------------------------------

note: To check for compile-time only dependencies, re-run hp-check with the -c parameter (ie, hp-check -c).
note: To check for run-time only dependencies, re-run hp-check with the -r parameter (ie, hp-check -r).

Checking for dependency: CUPS - Common Unix Printing System...
OK, found.

Checking for dependency: CUPS DDK - CUPS driver development kit...
OK, found.

Checking for dependency: CUPS devel- Common Unix Printing System development files...
error: NOT FOUND! This is a REQUIRED/COMPILE TIME ONLY dependency. Please make sure that this dependency is installed before installing or running HPLIP.
To install this dependency, execute this command:
sudo aptitude install --assume-yes libcupsys2-dev cupsys-bsd

Checking for dependency: DBus - Message bus system...
error: NOT FOUND! This is a REQUIRED dependency. Please make sure that this dependency is installed before installing or running HPLIP.
To install this dependency, execute this command:
sudo aptitude install --assume-yes libdbus-1-dev

Checking for dependency: gcc - GNU Project C and C++ Compiler...
error: NOT FOUND! This is a REQUIRED/COMPILE TIME ONLY dependency. Please make sure that this dependency is installed before installing or running HPLIP.
To install this dependency, execute this command:
sudo aptitude install --assume-yes build-essential

Checking for dependency: GhostScript - PostScript and PDF language interpreter and previewer...
OK, found.

Checking for dependency: libcrypto - OpenSSL cryptographic library...
error: NOT FOUND! This is a REQUIRED dependency. Please make sure that this dependency is installed before installing or running HPLIP.
To install this dependency, execute this command:
sudo aptitude install --assume-yes openssl

Checking for dependency: libjpeg - JPEG library...
error: NOT FOUND! This is a REQUIRED dependency. Please make sure that this dependency is installed before installing or running HPLIP.
To install this dependency, execute this command:
sudo aptitude install --assume-yes libjpeg62-dev

Checking for dependency: libnetsnmp-devel - SNMP networking library development files...
error: NOT FOUND! This is a REQUIRED dependency. Please make sure that this dependency is installed before installing or running HPLIP.
To install this dependency, execute this command:
sudo aptitude install --assume-yes libsnmp-dev

Checking for dependency: libpthread - POSIX threads library...
OK, found.

Checking for dependency: libtool - Library building support services...
error: NOT FOUND! This is a REQUIRED/COMPILE TIME ONLY dependency. Please make sure that this dependency is installed before installing or running HPLIP.
To install this dependency, execute this command:
sudo aptitude install --assume-yes libtool

Checking for dependency: libusb - USB library...
error: NOT FOUND! This is a REQUIRED dependency. Please make sure that this dependency is installed before installing or running HPLIP.
To install this dependency, execute this command:
sudo aptitude install --assume-yes libusb-dev

Checking for dependency: make - GNU make utility to maintain groups of programs...
OK, found.

Checking for dependency: PIL - Python Imaging Library (required for commandline scanning with hp-scan)...
OK, found.

Checking for dependency: ppdev - Parallel port support kernel module....
OK, found.

Checking for dependency: PyQt 4- Qt interface for Python (for Qt version 4.x)...
OK, found.

Checking for dependency: PyQt 4 DBus - DBus Support for PyQt4...
OK, found.

Checking for dependency: Python ctypes - A foreign function library for Python...
OK, found.

Checking for dependency: Python DBus - Python bindings for DBus...
OK, found.

Checking for dependency: Python devel - Python development files...
error: NOT FOUND! This is a REQUIRED/COMPILE TIME ONLY dependency. Please make sure that this dependency is installed before installing or running HPLIP.
To install this dependency, execute this command:
sudo aptitude install --assume-yes python2.5-dev

Checking for dependency: Python XML libraries...
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
error: NOT FOUND! This is a REQUIRED/COMPILE TIME ONLY dependency. Please make sure that this dependency is installed before installing or running HPLIP.
To install this dependency, execute this command:
sudo aptitude install --assume-yes libsane-dev

Checking for dependency: scanimage - Shell scanning program...
OK, found.

Checking for dependency: xsane - Graphical scanner frontend for SANE...
OK, found.


----------------------
| HPLIP INSTALLATION |
----------------------


Currently installed HPLIP version...
HPLIP 3.9.2 currently installed in '/usr/share/hplip'.

Current contents of '/etc/hp/hplip.conf' file:
# hplip.conf.  Generated from hplip.conf.in by configure.

[hplip]
version=3.9.2

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
internal-tag=3.9.2.49
restricted-build=no
ui-toolkit=qt4
qt3=no
qt4=yes




Current contents of '~/.hplip/hplip.conf' file:
[last_used]
printer_name = HP-PSC-2150
printer = 
device_uri = hp:/usb/PSC_2170_Series?serial=MY43VF536N73

[commands]
scan = /usr/bin/xsane -V %SANE_URI%

[installation]
version = 3.9.2.49
date_time = 05/27/09 18:14:05

[settings]
systray_visible = 0

[refresh]
rate = 30
enable = true
type = 1

[polling]
enable = false
device_list = 
interval = 5



-------------------------------
| DISCOVERED PARALLEL DEVICES |
-------------------------------

No devices found.

--------------------------
| DISCOVERED USB DEVICES |
--------------------------

  Device URI                        Model             
  --------------------------------  ------------------
  hp:/usb/PSC_2170_Series?serial=M  HP PSC 2170 Series
  Y43VF536N73                                         

---------------------------------
| INSTALLED CUPS PRINTER QUEUES |
---------------------------------

 
PSC_2170
--------
Type: Printer
Installed in HPLIP?: Yes, using the hp: CUPS backend.
Device URI: hp:/usb/PSC_2170_Series?serial=MY43VF536N73
PPD: /etc/cups/ppd/PSC_2170.ppd
PPD Description: HP PSC 500 Foomatic/pcl3
Printer status: printer PSC_2170 now printing PSC_2170-0.  enabled since Wed 27 May 2009 08:04:43 BST
Communication status: Good


----------------------
| SANE CONFIGURATION |
----------------------

'hpaio' in '/etc/sane.d/dll.conf'...
'hpaio' in '/etc/sane.d/dll.d/hplip'...
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
 
HP Device 0x2b11 at 003:002: 
    Device URI: hp:/usb/PSC_2170_Series?serial=MY43VF536N73
    Device node: /dev/bus/usb/003/002
    Mode: 0664
getfacl: Removing leading '/' from absolute path names
# file: dev/bus/usb/003/002
# owner: root
# group: lp
user::rw-
user:ed:rw-
group::rw-
mask::rw-
other::r--



-----------
| SUMMARY |
-----------

error: 11 errors and/or warnings.

Summary of needed commands to run to satisfy missing dependencies:
sudo aptitude install --assume-yes libcupsys2-dev cupsys-bsd
sudo aptitude install --assume-yes libdbus-1-dev
sudo aptitude install --assume-yes build-essential
sudo aptitude install --assume-yes openssl
sudo aptitude install --assume-yes libjpeg62-dev
sudo aptitude install --assume-yes libsnmp-dev
sudo aptitude install --assume-yes libtool
sudo aptitude install --assume-yes libusb-dev
sudo aptitude install --assume-yes python2.5-dev
sudo aptitude install --assume-yes libsane-dev

Please refer to the installation instructions at:
[http://hplip.sourceforge.net/install/index.html](http://hplip.sourceforge.net/install/index.html)


Done.

---

### Post by drifter129 on 2009-05-27
resolved this by flushing buffer on printer.
there may have been some job holding things up in the printer memory.

---

