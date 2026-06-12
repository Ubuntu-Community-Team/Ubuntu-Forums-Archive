---
title: "HP d1660 not printing"
date: 2010-09-01
forum: Hardware
---

### Post by brittanie on 2010-09-01
All seems to be in working order. Printing in process and printing complete come up in top right corner, but will not print. Here is what hp-check -t came back with:

Initializing. Please wait...

---------------
| SYSTEM INFO |
---------------

Basic system information:
Linux bunbunderson-laptop 2.6.32-24-generic #41-Ubuntu SMP Thu Aug 19 01:12:52 UTC 2010 i686 GNU/Linux

Distribution:
ubuntu 10.04

Checking Python version...
OK, version 2.6.5 installed

Checking PyQt 4.x version...
OK, version 4.7.2 installed.

Checking for CUPS...
Status: scheduler is running
Version: 1.4.3
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

Checking for dependency: PyQt 4 DBus - DBus Support for PyQt4...
OK, found.

Checking for dependency: Python DBus - Python bindings for DBus...
OK, found.

Checking for dependency: Python devel - Python development files...
OK, found.

Checking for dependency: Python libnotify - Python bindings for the libnotify Desktop notifications...
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
HPLIP 3.10.2 currently installed in '/usr/share/hplip'.

Current contents of '/etc/hp/hplip.conf' file:
# hplip.conf. Generated from hplip.conf.in by configure.

[hplip]
version=3.10.2

[dirs]
home=/usr/share/hplip
run=/var/run
ppd=/usr/share/ppd/hplip/HP
ppdbase=/usr/share/ppd/hplip
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
hpijs-install=yes
foomatic-drv-install=yes
foomatic-ppd-install=yes
foomatic-rip-hplip-install=no
hpcups-install=yes
cups-drv-install=yes
cups-ppd-install=no
internal-tag=3.10.2rc1.9
restricted-build=no
ui-toolkit=qt4
qt3=no
qt4=yes
policy-kit=yes
hpijs-only-build=no
lite-build=no
udev-acl-rules=yes
hpcups-only-build=no
hpijs-only-build=no

Current contents of '/var/lib/hp/hplip.state' file:
# hplip.state - HPLIP runtime persistent variables.

[plugin]
installed=0
eula=0

Current contents of '~/.hplip/hplip.conf' file:
[last_used]
printer_name = Deskjet_D1600
working_dir = .
device_uri = "hp:/usb/Deskjet_D1600_series?serial=CN9C1C94TW05CT"

[commands]
scan = /usr/bin/simple-scan %SANE_URI%

[installation]
version = 3.10.2rc1.9
date_time = 08/31/2010 20:54:08

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

--------------------------
| DISCOVERED USB DEVICES |
--------------------------

  Device URI Model
  -------------------------------- -----------------------
  hp:/usb/Deskjet_D1600_series?ser HP Deskjet D1600 series
  ial=CN9C1C94TW05CT

---------------------------------
| INSTALLED CUPS PRINTER QUEUES |
---------------------------------

Deskjet_D1600
-------------
Type: Printer
Device URI: hp:/usb/Deskjet_D1600_series?serial=CN9C1C94TW05CT
PPD: /etc/cups/ppd/Deskjet_D1600.ppd
PPD Description: HP Deskjet d1600 Series hpijs, 3.10.2
Printer status: printer Deskjet_D1600 is idle. enabled since Tue 31 Aug 2010 08:47:46 Pready to print
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

HP Device 0x7f11 at 002:002:
    Device URI: hp:/usb/Deskjet_D1600_series?serial=CN9C1C94TW05CT
    Device node: /dev/bus/usb/002/002
    Mode: 0664

---------------
| USER GROUPS |
---------------

bunbunderson adm dialout cdrom plugdev lpadmin admin sambashare

error: User needs to be member of group 'lp' to enable print, scan & fax.
User member of group 'lpadmin'.

-----------
| SUMMARY |
-----------

No errors or warnings.

Done.

Any help would be great!

---

