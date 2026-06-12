---
title: "hplip 3.9.4b Can't find HP Deskjet 722C in Jaunty"
date: 2009-05-25
forum: Hardware
---

### Post by uutnubu on 2009-05-25
Installed, reinstalled, changed BIOS settings, no luck.  The HP device manager will not find the 722C on the parallel port.

Ran the hp-check -t, results follow

OBTW I installed the borrowed USB printer just to see if hplip would work at all.  It does, :grin:  just can't find my printer on the parallel port :sad:.
---------------
| SYSTEM INFO |
---------------

Basic system information:
Linux jim-desktop 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686 GNU/Linux

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

Checking for dependency: CUPS image - CUPS image development files...
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

Checking for dependency: PolicyKit - Administrative policy framework...
OK, found.

Checking for dependency: ppdev - Parallel port support kernel module....
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
HPLIP 3.9.4b currently installed in '/usr/share/hplip'.

Current contents of '/etc/hp/hplip.conf' file:
# hplip.conf.  Generated from hplip.conf.in by configure.

[hplip]
version=3.9.4b

[dirs]
home=/usr/share/hplip
run=/var/run
ppd=/usr/share/ppd/hpijs/HP
ppdbase=/usr/share/ppd/hpijs
doc=/usr/share/doc/hplip-3.9.4b
icon=/usr/share/applications
cupsbackend=/usr/lib/cups/backend
cupsfilter=/usr/lib/cups/filter
drv=/usr/share/cups/drv/hp/

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
cups-ppd-install=no
cups-drv-install=no
internal-tag=3.9.4b.10
restricted-build=no
ui-toolkit=qt4
qt3=no
qt4=yes
policy-kit=yes


Current contents of '/var/lib/hp/hplip.state' file:
[plugin]
eula = 1
installed = 1



Current contents of '~/.hplip/hplip.conf' file:
[last_used]
printer_name = 
working_dir = .
device_uri = "hp:/usb/PSC_2200_Series?serial=MY31BB33510G"

[commands]
scan = /usr/bin/xsane -V %SANE_URI%

[installation]
version = 3.9.4b.10
date_time = 05/25/09 08:34:51

[settings]
systray_messages = 0
systray_visible = 0

[fax]
email_address = 
voice_phone = 

[refresh]
rate = 30
enable = false
type = 1

[polling]
enable = false
device_list = 
interval = 5



-------------------------------
| DISCOVERED PARALLEL DEVICES |
-------------------------------

No devices found.

[COLOR=Red](note:  Yes it's plugged in, and turned on)[/COLOR]

--------------------------
| DISCOVERED USB DEVICES |
--------------------------

  Device URI                        Model             
  --------------------------------  ------------------
  hp:/usb/PSC_2200_Series?serial=M  HP PSC 2200 Series
  Y31BB33510G                                         

---------------------------------
| INSTALLED CUPS PRINTER QUEUES |
---------------------------------

 
PSC-2200-Series
---------------
Type: Printer
Device URI: hp:/usb/PSC_2200_Series?serial=MY31BB33510G
PPD: /etc/cups/ppd/PSC-2200-Series.ppd
PPD Description: HP PSC 2200 Series hpijs, 3.9.4b
Printer status: printer PSC-2200-Series is idle.  enabled since Mon 25 May 2009 08:21:35 AM EDT
Communication status: Good

PSC_2200
--------
Type: Printer
Device URI: hp:/usb/PSC_2200_Series?serial=MY31BB33510G
PPD: /etc/cups/ppd/PSC_2200.ppd
PPD Description: HP PSC 2200 Series hpijs, 3.9.4b
Printer status: printer PSC_2200 is idle.  enabled since Mon 25 May 2009 08:14:22 AM EDT
Communication status: Good

PSC_2200_fax
------------
Type: Fax
Device URI: hpfax:/usb/PSC_2200_Series?serial=MY31BB33510G
PPD: /etc/cups/ppd/PSC_2200_fax.ppd
PPD Description: HP Fax
Printer status: printer PSC_2200_fax is idle.  enabled since Mon 25 May 2009 08:13:30 AM EDT
Communication status: Good


----------------------
| SANE CONFIGURATION |
----------------------

'hpaio' in '/etc/sane.d/dll.conf'...
OK, found. SANE backend 'hpaio' is properly set up.

Checking output of 'scanimage -L'...
device `hpaio:/usb/PSC_2200_Series?serial=MY31BB33510G' is a Hewlett-Packard PSC_2200_Series all-in-one


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

HP Device 0x2911 at 005:002: 
    Device URI: hp:/usb/PSC_2200_Series?serial=MY31BB33510G
    Device node: /dev/bus/usb/005/002
    Mode: 0660
getfacl: Removing leading '/' from absolute path names
# file: dev/bus/usb/005/002
# owner: lp
# group: lp
user::rw-
user:jim:rw-
group::rw-
mask::rw-
other::---



---------------
| USER GROUPS |
---------------

jim adm dialout cdrom plugdev lpadmin admin sambashare


-----------
| SUMMARY |
-----------

No errors or warnings.

Done.

---

### Post by 11hjpphty76lkjj on 2009-05-25
This help at all?
[URL="http://hplipopensource.com/node/217"]
http://hplipopensource.com/node/217[/URL]

---

### Post by uutnubu on 2009-05-25
Thanks, but no help, went thru all of the suggested steps, but hp-setup still can't find the Deskjet 722 on the parallel port.

---

### Post by uutnubu on 2009-05-26
Also tried earlier versions of hplip with no success either.

---

