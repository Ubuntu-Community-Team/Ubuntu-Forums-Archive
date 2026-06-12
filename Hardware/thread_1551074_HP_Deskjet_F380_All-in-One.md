---
title: "HP Deskjet F380 All-in-One"
date: 2010-08-11
forum: Hardware
---

### Post by boondocks on 2010-08-11
This is a dual-boot system with XP and Ubuntu 9.04 where Ubuntu was installed with Wubi.
I am trying to help a family member with the HP Deskjet F380 All-in-One.

On the XP side, printing and scanning works fine.

With Ubuntu 9.04:
The printing works fine.
The scanning is the problem.

I get messages like:
[INDENT]error: Unable to connect to dbus session bus.
error: Unable to communicate with device (code=12): hp:/usb/Deskjet_F300_series?serial=CNxxxxxxxx
error: Device not found
[/INDENT]
So I did a "hp-check"```
hp-check[7584]: info: :
Initializing. Please wait...
Ubuntu

9.04

scheduler is running

1.3.9

Linux fjubuntu 2.6.28-19-generic #62-Ubuntu SMP Wed Jul 28 01:56:51 UTC 2010 i686 GNU/Linux

hp-check[7584]: info: :
hp-check[7584]: info: :---------------
hp-check[7584]: info: :| SYSTEM INFO |
hp-check[7584]: info: :---------------
hp-check[7584]: info: :
hp-check[7584]: info: :Basic system information:
hp-check[7584]: info: :Linux fjubuntu 2.6.28-19-generic #62-Ubuntu SMP Wed Jul 28 01:56:51 UTC 2010 i686 GNU/Linux
hp-check[7584]: info: :
hp-check[7584]: info: :Distribution:
hp-check[7584]: info: :ubuntu 9.04
hp-check[7584]: info: :
HPOJ running?
hp-check[7584]: info: :No, HPOJ is not running (OK).
hp-check[7584]: info: :
hp-check[7584]: info: :Checking Python version...
hp-check[7584]: info: :OK, version 2.6.2 installed
hp-check[7584]: info: :
hp-check[7584]: info: :Checking PyQt 4.x version...
hp-check[7584]: info: :OK, version 4.4.4 installed.
hp-check[7584]: info: :
hp-check[7584]: info: :Checking for CUPS...
hp-check[7584]: info: :Status: scheduler is running
hp-check[7584]: info: :Version: 1.3.9
hp-check[7584]: info: :error_log is set to level: warn
hp-check[7584]: info: :
hp-check[7584]: info: :Checking for dbus/python-dbus...
hp-check[7584]: info: :dbus daemon is running.
hp-check[7584]: info: :python-dbus version: 0.83.0
hp-check[7584]: info: :
hp-check[7584]: info: :
hp-check[7584]: info: :------------------------------------
hp-check[7584]: info: :| COMPILE AND RUNTIME DEPENDENCIES |
hp-check[7584]: info: :------------------------------------
hp-check[7584]: info: :
note: To check for compile-time only dependencies, re-run hp-check with the -c parameter (ie, hp-check -c).
note: To check for run-time only dependencies, re-run hp-check with the -r parameter (ie, hp-check -r).
hp-check[7584]: info: :
hp-check[7584]: info: :Checking for dependency: CUPS - Common Unix Printing System...
hp-check[7584]: info: :OK, found.
hp-check[7584]: info: :
hp-check[7584]: info: :Checking for dependency: CUPS DDK - CUPS driver development kit...
hp-check[7584]: info: :OK, found.
hp-check[7584]: info: :
hp-check[7584]: info: :Checking for dependency: CUPS devel- Common Unix Printing System development files...
hp-check[7584]: info: :OK, found.
hp-check[7584]: info: :
hp-check[7584]: info: :Checking for dependency: DBus - Message bus system...
hp-check[7584]: info: :OK, found.
hp-check[7584]: info: :
hp-check[7584]: info: :Checking for dependency: gcc - GNU Project C and C++ Compiler...
hp-check[7584]: info: :OK, found.
hp-check[7584]: info: :
hp-check[7584]: info: :Checking for dependency: GhostScript - PostScript and PDF language interpreter and previewer...
hp-check[7584]: info: :OK, found.
hp-check[7584]: info: :
hp-check[7584]: info: :Checking for dependency: libcrypto - OpenSSL cryptographic library...
hp-check[7584]: info: :OK, found.
hp-check[7584]: info: :
hp-check[7584]: info: :Checking for dependency: libjpeg - JPEG library...
hp-check[7584]: info: :OK, found.
hp-check[7584]: info: :
hp-check[7584]: info: :Checking for dependency: libnetsnmp-devel - SNMP networking library development files...
hp-check[7584]: info: :OK, found.
hp-check[7584]: info: :
hp-check[7584]: info: :Checking for dependency: libpthread - POSIX threads library...
hp-check[7584]: info: :OK, found.
hp-check[7584]: info: :
hp-check[7584]: info: :Checking for dependency: libtool - Library building support services...
hp-check[7584]: info: :OK, found.
hp-check[7584]: info: :
hp-check[7584]: info: :Checking for dependency: libusb - USB library...
hp-check[7584]: info: :OK, found.
hp-check[7584]: info: :
hp-check[7584]: info: :Checking for dependency: make - GNU make utility to maintain groups of programs...
hp-check[7584]: info: :OK, found.
hp-check[7584]: info: :
hp-check[7584]: info: :Checking for dependency: PIL - Python Imaging Library (required for commandline scanning with hp-scan)...
hp-check[7584]: info: :OK, found.
hp-check[7584]: info: :
hp-check[7584]: info: :Checking for dependency: ppdev - Parallel port support kernel module....
hp-check[7584]: info: :OK, found.
hp-check[7584]: info: :
hp-check[7584]: info: :Checking for dependency: PyQt 4- Qt interface for Python (for Qt version 4.x)...
hp-check[7584]: info: :OK, found.
hp-check[7584]: info: :
hp-check[7584]: info: :Checking for dependency: PyQt 4 DBus - DBus Support for PyQt4...
hp-check[7584]: info: :OK, found.
hp-check[7584]: info: :
hp-check[7584]: info: :Checking for dependency: Python ctypes - A foreign function library for Python...
hp-check[7584]: info: :OK, found.
hp-check[7584]: info: :
hp-check[7584]: info: :Checking for dependency: Python DBus - Python bindings for DBus...
hp-check[7584]: info: :OK, found.
hp-check[7584]: info: :
hp-check[7584]: info: :Checking for dependency: Python devel - Python development files...
hp-check[7584]: info: :OK, found.
hp-check[7584]: info: :
hp-check[7584]: info: :Checking for dependency: Python XML libraries...
hp-check[7584]: info: :OK, found.
hp-check[7584]: info: :
hp-check[7584]: info: :Checking for dependency: Python 2.3 or greater - Required for fax functionality...
hp-check[7584]: info: :OK, found.
hp-check[7584]: info: :
hp-check[7584]: info: :Checking for dependency: Python 2.2 or greater - Python programming language...
hp-check[7584]: info: :OK, found.
hp-check[7584]: info: :
hp-check[7584]: info: :Checking for dependency: Reportlab - PDF library for Python...
hp-check[7584]: info: :OK, found.
hp-check[7584]: info: :
hp-check[7584]: info: :Checking for dependency: SANE - Scanning library...
hp-check[7584]: info: :OK, found.
hp-check[7584]: info: :
hp-check[7584]: info: :Checking for dependency: SANE - Scanning library development files...
hp-check[7584]: info: :OK, found.
hp-check[7584]: info: :
hp-check[7584]: info: :Checking for dependency: scanimage - Shell scanning program...
hp-check[7584]: info: :OK, found.
hp-check[7584]: info: :
hp-check[7584]: info: :Checking for dependency: xsane - Graphical scanner frontend for SANE...
hp-check[7584]: info: :OK, found.
hp-check[7584]: info: :
hp-check[7584]: info: :
hp-check[7584]: info: :----------------------
hp-check[7584]: info: :| HPLIP INSTALLATION |
hp-check[7584]: info: :----------------------
hp-check[7584]: info: :
hp-check[7584]: info: :
hp-check[7584]: info: :Currently installed HPLIP version...
hp-check[7584]: info: :HPLIP 3.9.2 currently installed in '/usr/share/hplip'.
hp-check[7584]: info: :
hp-check[7584]: info: :Current contents of '/etc/hp/hplip.conf' file:
hp-check[7584]: info: :# hplip.conf.  Generated from hplip.conf.in by configure.

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



hp-check[7584]: info: :
hp-check[7584]: info: :Current contents of '~/.hplip/hplip.conf' file:
hp-check[7584]: info: :[last_used]
device_uri = hp:/usb/Deskjet_F300_series?serial=CNxxxxxxxx

[installation]
version = 3.9.2.49
date_time = 08/12/10 04:28:58


hp-check[7584]: info: :
hp-check[7584]: info: :-------------------------------
hp-check[7584]: info: :| DISCOVERED PARALLEL DEVICES |
hp-check[7584]: info: :-------------------------------
hp-check[7584]: info: :
hp-check[7584]: info: :No devices found.
hp-check[7584]: info: :
hp-check[7584]: info: :--------------------------
hp-check[7584]: info: :| DISCOVERED USB DEVICES |
hp-check[7584]: info: :--------------------------
hp-check[7584]: info: :
hp-check[7584]: info: :No devices found.
hp-check[7584]: info: :
hp-check[7584]: info: :---------------------------------
hp-check[7584]: info: :| INSTALLED CUPS PRINTER QUEUES |
hp-check[7584]: info: :---------------------------------
hp-check[7584]: info: :
hp-check[7584]: info: :
hp-check[7584]: info: :Deskjet-F300-series
hp-check[7584]: info: :-------------------
hp-check[7584]: info: :Type: Printer
hp-check[7584]: info: :Installed in HPLIP?: Yes, using the hp: CUPS backend.
hp-check[7584]: info: :Device URI: hp:/usb/Deskjet_F300_series?serial=CNxxxxxxxx
hp-check[7584]: info: :PPD: /etc/cups/ppd/Deskjet-F300-series.ppd
hp-check[7584]: info: :PPD Description: HP Deskjet f300 Series hpijs, 3.9.2
hp-check[7584]: info: :Printer status: printer Deskjet-F300-series is idle.  enabled since Fri 23 Jul 2010 04:41:29 PM GST
error: Unable to connect to dbus session bus.
error: Unable to communicate with device (code=12): hp:/usb/Deskjet_F300_series?serial=CNxxxxxxxx
error: Device not found
hp-check[7584]: info: :
hp-check[7584]: info: :
hp-check[7584]: info: :----------------------
hp-check[7584]: info: :| SANE CONFIGURATION |
hp-check[7584]: info: :----------------------
hp-check[7584]: info: :
hp-check[7584]: info: :'hpaio' in '/etc/sane.d/dll.conf'...
hp-check[7584]: info: :'hpaio' in '/etc/sane.d/dll.d/hplip'...
hp-check[7584]: info: :OK, found. SANE backend 'hpaio' is properly set up.
hp-check[7584]: info: :
hp-check[7584]: info: :Checking output of 'scanimage -L'...
hp-check[7584]: info: :
No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).

hp-check[7584]: info: :
hp-check[7584]: info: :---------------------
hp-check[7584]: info: :| PYTHON EXTENSIONS |
hp-check[7584]: info: :---------------------
hp-check[7584]: info: :
hp-check[7584]: info: :Checking 'cupsext' CUPS extension...
hp-check[7584]: info: :OK, found.
hp-check[7584]: info: :
hp-check[7584]: info: :Checking 'pcardext' Photocard extension...
hp-check[7584]: info: :OK, found.
hp-check[7584]: info: :
hp-check[7584]: info: :Checking 'hpmudext' I/O extension...
hp-check[7584]: info: :OK, found.
hp-check[7584]: info: :
hp-check[7584]: info: :Checking 'scanext' SANE scanning extension...
hp-check[7584]: info: :OK, found.
hp-check[7584]: info: :
hp-check[7584]: info: :
hp-check[7584]: info: :-----------------
hp-check[7584]: info: :| USB I/O SETUP |
hp-check[7584]: info: :-----------------
hp-check[7584]: info: :
hp-check[7584]: info: :
hp-check[7584]: info: :Checking for permissions of USB attached printers...
hp-check[7584]: info: :
HP Device 0x5511 at 001:002: 
warning:     Device URI: (Makeuri FAILED)
hp-check[7584]: info: :    Device node: /dev/bus/usb/001/002
hp-check[7584]: info: :    Mode: 0664
hp-check[7584]: info: :getfacl: Removing leading '/' from absolute path names
# file: dev/bus/usb/001/002
# owner: root
# group: lp
user::rw-
group::rw-
other::r--


hp-check[7584]: info: :
hp-check[7584]: info: :-----------
hp-check[7584]: info: :| SUMMARY |
hp-check[7584]: info: :-----------
hp-check[7584]: info: :
error: 1 error or warning.
hp-check[7584]: info: :
hp-check[7584]: info: :Please refer to the installation instructions at:
hp-check[7584]: info: :http://hplip.sourceforge.net/install/index.html

hp-check[7584]: info: :
hp-check[7584]: info: :Done.
```
Any help would be appreciated.

---

