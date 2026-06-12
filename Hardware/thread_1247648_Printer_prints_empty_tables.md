---
title: "Printer prints empty tables"
date: 2009-08-23
forum: Hardware
---

### Post by Stoneface on 2009-08-23
On my Ubuntu Jaunty Jackalope OS I replugged my HP Deskjet F4275 inkjet printer after having not used it for quite a while. Last time was on hardy I believe..
Ubuntu recognized the printer right away so all seemed ok. Then I printed some pages from Open Office Writer 3.0. Ubuntu indicated they were printed, but they weren't. Then I removed some printers that were no longer there and unplugged and plugged the current printer again as it somehow got disconnected. 
I printed the pages again. This time the printer did print but only empty tables! I made some vocabulary lists in columns. The table borders or the table framework was printed, but no vocabulary! Why?
I printed a regular text pages from OO as well and printing was successful according to Ubuntu, but nothing was printed!! What is going on here?

FYI I do have hplib-data, hplip installed, 

```

lpq
Deskjet-F4200-series is ready
no entries
```

and
```

me@me-laptop:/var/log$ dmesg | grep printer
[59404.194556] usblp0: USB Bidirectional printer dev 6 if 1 alt 0 proto 2 vid 0x03F0 pid 0x2504
[60011.100907] usblp0: USB Bidirectional printer dev 7 if 1 alt 0 proto 2 vid 0x03F0 pid 0x2504
[61551.999146] usblp0: USB Bidirectional printer dev 8 if 1 alt 0 proto 2 vid 0x03F0 pid 0x2504

```

tail user log:
```
Aug 22 22:11:00 me-laptop python: hp-systray[5000]: error: Unable to open /home/me/.hplip/hp-systray.lock lock file.
Aug 23 14:43:15 me-laptop hpijs: WARNING: black pen has low ink 
Aug 23 14:43:15 me-laptop hpijs: STATE: marker-supply-low-warning 
Aug 23 14:49:17 me-laptop hpijs: unable to write to output, fd=10, count=4096: Broken pipe 
Aug 23 14:49:17 me-laptop last message repeated 4 times
Aug 23 14:54:25 me-laptop python: hp-info[19548]: warning: No display found.
Aug 23 14:54:25 me-laptop python: hp-info[19548]: error: hp-info -u/--gui requires Qt4 GUI support. Entering interactive mode.
Aug 23 14:54:25 me-laptop python: hp-systray[19549]: warning: No display found.
Aug 23 14:54:25 me-laptop python: hp-systray[19549]: error: hp-systray requires Qt4 GUI and DBus support. Exiting.
Aug 23 14:54:29 me-laptop python: hp-info[19548]: warning: Unable to connect to dbus. Is hp-systray running?
Aug 23 14:56:12 me-laptop Deskjet_F4200_series?serial=CN872291W805BR: io/hpmud/musb.c 1381: unable to write data hp:/usb/Deskjet_F4200_series?serial=CN872291W805BR: 45 second io timeout 
```

---

### Post by Stoneface on 2009-08-23
tried to uninstall and reinstall hplib via the HP Linux Drivers site. Got this error during installation:

Configure failed with error: python-devel not found

---

### Post by Stoneface on 2009-08-23
After the installation failed I did a  sudo hp-check -t
 (had to reinstall hplip-data) and this came out:

```

HP Linux Imaging and Printing System (ver. 3.9.2)
Dependency/Version Check Utility ver. 14.1

Copyright (c) 2001-8 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

Note: hp-check can be run in three modes:
1. Compile-time check mode (-c or --compile): Use this mode before compiling the HPLIP supplied tarball (.tar.gz or   
.run) to determine if the proper dependencies are installed to successfully compile HPLIP.                            
2. Run-time check mode (-r or --run): Use this mode to determine if a distro supplied package (.deb, .rpm, etc) or an 
already built HPLIP supplied tarball has the proper dependencies installed to successfully run.                       
3. Both compile- and run-time check mode (-b or --both) (Default): This mode will check both of the above cases (both 
compile- and run-time dependencies).                                                                                  

Saving output in log file: hp-check.log

Initializing. Please wait...
 
---------------
| SYSTEM INFO |
---------------

Basic system information:
Linux jasper-laptop 2.6.28-15-generic #49-Ubuntu SMP Tue Aug 18 18:40:08 UTC 2009 i686 GNU/Linux

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
Version: 1.3.9
error_log is set to level: warn

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
OK, found.

Checking for dependency: DBus - Message bus system...
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

Checking for dependency: PyQt 4- Qt interface for Python (for Qt version 4.x)...
OK, found.

Checking for dependency: PyQt 4 DBus - DBus Support for PyQt4...
OK, found.

Checking for dependency: Python ctypes - A foreign function library for Python...
OK, found.

Checking for dependency: Python DBus - Python bindings for DBus...
OK, found.

Checking for dependency: Python devel - Python development files...
OK, found.

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
OK, found.

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
device_uri = hp:/usb/Deskjet_F4200_series?serial=CN872291W805BR

[installation]
version = 2.8.2.10
date_time = 03/31/09 09:10:34



-------------------------------
| DISCOVERED PARALLEL DEVICES |
-------------------------------

No devices found.

--------------------------
| DISCOVERED USB DEVICES |
--------------------------

  Device URI                                       Model                  
  -----------------------------------------------  -----------------------
  hp:/usb/Deskjet_F4200_series?serial=CN872291W80  HP Deskjet F4200 series
  5BR                                                                     

---------------------------------
| INSTALLED CUPS PRINTER QUEUES |
---------------------------------

 
Deskjet-F4200-series
--------------------
Type: Printer
Installed in HPLIP?: Yes, using the hp: CUPS backend.
Device URI: hp:/usb/Deskjet_F4200_series?serial=CN872291W805BR
PPD: /etc/cups/ppd/Deskjet-F4200-series.ppd
PPD Description: HP Deskjet f4200 Series hpijs, 3.9.2
Printer status: printer Deskjet-F4200-series is idle.  enabled since Sun 23 Aug 2009 04:30:40 PM MSD
Communication status: Good


----------------------
| SANE CONFIGURATION |
----------------------

'hpaio' in '/etc/sane.d/dll.conf'...
'hpaio' in '/etc/sane.d/dll.d/hplip'...
OK, found. SANE backend 'hpaio' is properly set up.

Checking output of 'scanimage -L'...
device `v4l:/dev/video0' is a Noname Acer CrystalEye webcam virtual device
device `hpaio:/usb/Deskjet_F4200_series?serial=CN872291W805BR' is a Hewlett-Packard Deskjet_F4200_series all-in-one


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
 
HP Device 0x2504 at 001:009: 
    Device URI: hp:/usb/Deskjet_F4200_series?serial=CN872291W805BR
    Device node: /dev/bus/usb/001/009
    Mode: 0664
getfacl: Removing leading '/' from absolute path names
# file: dev/bus/usb/001/009
# owner: root
# group: root
user::rw-
group::rw-
mask::rw-
other::r--



-----------
| SUMMARY |
-----------

No errors or warnings.


```

---

### Post by Stoneface on 2009-08-23
I tried to print one more page and it could not find the printer. Here is the user log with errors:

```
Aug 23 16:42:05 me-laptop Deskjet_F4200_series?serial=CN872291W805BR: io/hpmud/musb.c 135: unable get_string_descriptor -1: Operation not permitted 
Aug 23 16:42:05 me-laptop Deskjet_F4200_series?serial=CN872291W805BR: io/hpmud/musb.c 603: invalid product id string ret=-1 
Aug 23 16:42:05 me-laptop Deskjet_F4200_series?serial=CN872291W805BR: io/hpmud/musb.c 1104: unable to open hp:/usb/Deskjet_F4200_series?serial=CN872291W805BR 
Aug 23 16:42:05 me-laptop Deskjet_F4200_series?serial=CN872291W805BR: prnt/backend/hp.c 676: INFO: open device failed stat=12; will retry in 30 seconds... 
Aug 23 16:42:06 me-laptop hpijs: io/hpmud/musb.c 135: unable get_string_descriptor -1: Operation not permitted 
Aug 23 16:42:06 me-laptop hpijs: io/hpmud/musb.c 603: invalid product id string ret=-1 
Aug 23 16:42:06 me-laptop hpijs: io/hpmud/musb.c 1104: unable to open hp:/usb/Deskjet_F4200_series?serial=CN872291W805BR 
Aug 23 16:42:35 me-laptop Deskjet_F4200_series?serial=CN872291W805BR: io/hpmud/musb.c 135: unable get_string_descriptor -1: Operation not permitted 
Aug 23 16:42:35 me-laptop Deskjet_F4200_series?serial=CN872291W805BR: io/hpmud/musb.c 603: invalid product id string ret=-1 
Aug 23 16:42:35 me-laptop Deskjet_F4200_series?serial=CN872291W805BR: io/hpmud/musb.c 1104: unable to open hp:/usb/Deskjet_F4200_series?serial=CN872291W805BR 
Aug 23 16:42:35 me-laptop Deskjet_F4200_series?serial=CN872291W805BR: prnt/backend/hp.c 676: INFO: open device failed stat=12; will retry in 30 seconds... 
Aug 23 16:43:05 me-laptop Deskjet_F4200_series?serial=CN872291W805BR: io/hpmud/musb.c 135: unable get_string_descriptor -1: Operation not permitted 
Aug 23 16:43:05 me-laptop Deskjet_F4200_series?serial=CN872291W805BR: io/hpmud/musb.c 603: invalid product id string ret=-1 
Aug 23 16:43:05 me-laptop Deskjet_F4200_series?serial=CN872291W805BR: io/hpmud/musb.c 1104: unable to open hp:/usb/Deskjet_F4200_series?serial=CN872291W805BR 
Aug 23 16:43:05 me-laptop Deskjet_F4200_series?serial=CN872291W805BR: prnt/backend/hp.c 676: INFO: open device failed stat=12; will retry in 30 seconds... 

```

The I unplugged and replugged and printed one page. It only printed empt cells again!!

Last user log errors were:
```

Aug 23 16:45:14 me-laptop hpijs: unable to write to output, fd=10, count=4096: Broken pipe 
Aug 23 16:45:14 me-laptop last message repeated 4 time

```

---

### Post by Stoneface on 2009-08-23
removed hplip again and did the installation with th HP installation file I downloaded for my model using this command: ```
sh hplip-3.9.8.run
```
And again this error: ```
error: Configure failed with error: python-devel not found
``` after a warning that a previous version was still and installed and would be overwritten because it could not be removed. of course it could not be removed cause I already did with ```
sudo apt-get remove --assume-yes hplip hpijs foomatic-db-hpijs
```
I don't get this at all...

---

### Post by Stoneface on 2009-09-06
Well it was partly my HP printer that was at fault. So this has been resolved by replacing cartridges and reinstalling all software. All is good now.

---

