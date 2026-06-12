---
title: "Printer stopped working after upgrading"
date: 2009-10-07
forum: Hardware
---

### Post by Camilia on 2009-10-07
After doing the upgrade my printer, hp deskjet 3930, stopped printing. It appears to print but nothing on the page. The options to troubleshoot it, print test and allignment, no longer available in the HP tool box. I know the cartridge is not empty for shortly before the problem I saw ink level in Tool box okay.

Did sudo hp-check -r
-------------
| SYSTEM INFO |
---------------

Basic system information:
Linux Brain 2.6.28-15-generic #52-Ubuntu SMP Wed Sep 9 10:49:34 UTC 2009 i686 GNU/Linux

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
error_log is set to level: info

Checking for dbus/python-dbus...
dbus daemon is running.
python-dbus version: 0.83.0


------------------------
| RUNTIME DEPENDENCIES |
------------------------


Checking for dependency: CUPS - Common Unix Printing System...
OK, found.

Checking for dependency: CUPS DDK - CUPS driver development kit...
OK, found.

Checking for dependency: GhostScript - PostScript and PDF language interpreter and previewer...
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

Checking for dependency: Python XML libraries...
OK, found.

Checking for dependency: Python 2.3 or greater - Required for fax functionality...
OK, found.

Checking for dependency: Reportlab - PDF library for Python...
OK, found.

Checking for dependency: SANE - Scanning library...
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
printer_name = Deskjet-3900
device_uri = hp:/usb/Deskjet_3900?serial=CN5CM1M2WY04DF

-------------------------------
| DISCOVERED PARALLEL DEVICES |
-------------------------------

No devices found.

--------------------------
| DISCOVERED USB DEVICES |
--------------------------

  Device URI                       Model          
  -------------------------------  ---------------
  hp:/usb/Deskjet_3900?serial=CN5  HP Deskjet 3900
  CM1M2WY04DF                                     

---------------------------------
| INSTALLED CUPS PRINTER QUEUES |
---------------------------------
Deskjet-3900
------------
Type: Printer
Installed in HPLIP?: Yes, using the hp: CUPS backend.
Device URI: hp:/usb/Deskjet_3900?serial=CN5CM1M2WY04DF
PPD: /etc/cups/ppd/Deskjet-3900.ppd
PPD Description: HP Deskjet 3900 hpijs, 3.9.2
Printer status: printer Deskjet-3900 is idle.  enabled since Wed 07 Oct 2009 12:34:47 AM EDT
Communication status: Good

Deskjet-39002
-------------
Type: Unknown
Installed in HPLIP?: No, not using the hp: or hpfax: CUPS backend.
Device URI: hal:///org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_02_0_if0_0_printer_CN5CM1M2WY04DF
PPD: /etc/cups/ppd/Deskjet-39002.ppd
PPD Description: HP Deskjet 3900 hpijs, 3.9.2
Printer status: printer Deskjet-39002 is idle.  enabled since Fri 02 Oct 2009 06:08:53 PM EDT
warning: Printer is not HPLIP installed. Printers must use the hp: or hpfax: CUPS backend to function in HPLIP.
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
----------------
Checking for permissions of USB attached printers...
HP Device 0x7604 at 002:004: 
    Device URI: hp:/usb/Deskjet_3900?serial=CN5CM1M2WY04DF
    Device node: /dev/bus/usb/002/004
    Mode: 0664
getfacl: Removing leading '/' from absolute path names
# file: dev/bus/usb/002/004
# owner: root
# group: lp
user::rw-
group::rw-
other::r--
-----------
| SUMMARY |
-----------

error: 1 error or warning.

Please refer to the installation instructions at:
[http://hplip.sourceforge.net/install/index.html](http://hplip.sourceforge.net/install/index.html)

Went to [http://hplip.sourceforge.net/install](http://hplip.sourceforge.net/install)
Followed the instructions to download installer.
Got Can't open hplip3.9.6run

Anybody know what I can do?

---

### Post by Camilia on 2009-10-10
After doing more upgrades everything is back to normal.

---

