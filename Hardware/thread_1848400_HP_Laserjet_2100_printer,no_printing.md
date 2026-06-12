---
title: "HP Laserjet 2100 printer,no printing"
date: 2011-09-22
forum: Hardware
---

### Post by Sevy on 2011-09-22
Ive installed my printer and everything seems fine including the test page but am unable to print anything else.The item in the print queue just stays on "processing" with the printer doing nothing

Ive installed HPLIP downloaded from the HP website which allows me to configure the printer and did it manually so as to enable parallel cable connection

Here is the output of hp-check -t

HP Linux Imaging and Printing System (ver. 3.11.7)
Dependency/Version Check Utility ver. 14.3

Copyright (c) 2001-9 Hewlett-Packard Development Company, LP
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
Linux sevy-desktop 2.6.38-11-generic #49-Ubuntu SMP Mon Aug 29 20:47:58 UTC 2011 i686 i686 i386 GNU/Linux

Distribution:
ubuntu 11.04

Checking Python version...
OK, version 2.7.1 installed

Checking PyQt 4.x version...
OK, version 4.8.3 installed.

Checking for CUPS...
Status: scheduler is running
Version: 1.4.6
error_log is set to level: warn

Checking for dbus/python-dbus...
dbus daemon is running.
python-dbus version: 0.83.1

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
HPLIP 3.11.7 currently installed in '/usr/share/hplip'.

Current contents of '/etc/hp/hplip.conf' file:
# hplip.conf. Generated from hplip.conf.in by configure.

[hplip]
version=3.11.7

[dirs]
home=/usr/share/hplip
run=/var/run
ppd=/usr/share/ppd/HP
ppdbase=/usr/share/ppd
doc=/usr/share/doc/hplip-3.11.7
icon=/usr/share/applications
cupsbackend=/usr/lib/cups/backend
cupsfilter=/usr/lib/cups/filter
drv=/usr/share/cups/drv/hp

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
hpijs-install=no
foomatic-drv-install=no
foomatic-ppd-install=no
foomatic-rip-hplip-install=no
hpcups-install=yes
cups-drv-install=yes
cups-ppd-install=no
internal-tag=3.11.7
restricted-build=no
ui-toolkit=qt4
qt3=no
qt4=yes
policy-kit=no
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
device_uri = "hp:/par/HP_LaserJet_2100_Series?device=/dev/parport0"
printer_name = Hewlett-Packard-HP-LaserJet-2100-Series
working_dir = .

[settings]
systray_visible = 0
systray_messages = 0

[commands]
scan = /usr/bin/xsane -V %SANE_URI%

[refresh]
rate = 10
enable = true
type = 1

[polling]
enable = false
interval = 5
device_list =

[fax]
voice_phone =
email_address =

[installation]
date_time = 11/09/11 19:04:36
version = 3.11.7

--------------------------
| DISCOVERED USB DEVICES |
--------------------------

No devices found.

---------------------------------
| INSTALLED CUPS PRINTER QUEUES |
---------------------------------

Hewlett-Packard-HP-LaserJet-2100-Series
---------------------------------------
Type: Printer
Device URI: hp:/par/HP_LaserJet_2100_Series?device=/dev/parport0
PPD: /etc/cups/ppd/Hewlett-Packard-HP-LaserJet-2100-Series.ppd
PPD Description: HP LaserJet 2100 Series Postscript (recommended)
Printer status: printer Hewlett-Packard-HP-LaserJet-2100-Series is idle. enabled since Sun 11 Sep 2011 18:19:04 BST

Any ideas ??

---

### Post by livemott on 2011-09-24
Check the USB line first, if no work, re-install drive

---

### Post by foresthill on 2011-09-24
Had the same problem with my HP 1320 Laserjet printer.

Try this:

[http://ubuntuforums.org/showpost.php?p=11255447&postcount=10](http://ubuntuforums.org/showpost.php?p=11255447&postcount=10)

(Of course you wanna choose your model from the list, not the 1320)

---

### Post by Sevy on 2011-09-26
> Check the USB line first, if no work, re-install drive 

The HP 2100 doesnt have a usb connection and I had to install HPLIP manually to enable parallel cable support

> Had the same problem with my HP 1320 Laserjet printer.

Try this:

[http://ubuntuforums.org/showpost.php...7&postcount=10](http://ubuntuforums.org/showpost.php...7&postcount=10)

(Of course you wanna choose your model from the list, not the 1320) 

Thanks foresthill,that seems to have done the trick.The only problem I have now is that the printer is in manual feed mode where I have to press the go button for every page I want to print.Nothing is mentioned in the manual other than it exists or how to change it to auto.
I cant find any configuration in printing preferences or HPLIP to change this.
In windows it starts in auto

---

### Post by foresthill on 2011-09-26
Glad that helped. :D

In Properties / Printer Options. there should be a "Paper Source" option. I remember on mine, I used to have to set it for "Tray 2" manually, since on my printer "Tray 1" is the manual feed slot. Now I just leave it set for "Automatic" and it works fine, but you might need to experiment and figure our which tray is the correct one.

---

### Post by Sevy on 2011-09-27
In printing preferences I have "media source" which enables me to select between "standard" , "manual" or different trays.
Ive tried all the options and each time I print the software tells me its printing and finished printing but no print from the printer itself.
Only when I press the go button on printer, it prints

---

