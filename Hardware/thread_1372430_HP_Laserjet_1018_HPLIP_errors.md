---
title: "HP Laserjet 1018 HPLIP errors"
date: 2010-01-04
forum: Hardware
---

### Post by JohnnyJonJon on 2010-01-04
When I pluged in the printer the setup runs smooth with no errors but at the point of printing a test page then nothing happens.  It says job submitted and processed but nothing comes out. As per HPLIP support here is the output of hp-test -t 

```
HP Linux Imaging and Printing System (ver. 3.9.8)
Dependency/Version Check Utility ver. 14.3

Copyright (c) 2001-9 Hewlett-Packard Development Company, LP
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
Linux boxtops 2.6.31-16-generic #53-Ubuntu SMP Tue Dec 8 04:01:29 UTC 2009 i686 GNU/Linux

Distribution:
ubuntu 9.10

Checking Python version...
OK, version 2.6.4 installed

Checking PyQt 4.x version...
error: NOT FOUND OR FAILED TO LOAD!

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
warning: NOT FOUND! This is an OPTIONAL/RUNTIME ONLY dependency. Some HPLIP functionality may not function properly.
To install this dependency, execute this command:
sudo aptitude install --assume-yes cupsddk cupsddk-drivers

Checking for dependency: CUPS devel- Common Unix Printing System development files...
error: NOT FOUND! This is a REQUIRED/COMPILE TIME ONLY dependency. Please make sure that this dependency is installed before installing or running HPLIP.
To install this dependency, execute this command:
sudo aptitude install --assume-yes libcupsys2-dev cupsys-bsd

Checking for dependency: CUPS image - CUPS image development files...
error: NOT FOUND! This is a REQUIRED/COMPILE TIME ONLY dependency. Please make sure that this dependency is installed before installing or running HPLIP.
To install this dependency, execute this command:
sudo aptitude install --assume-yes libcupsimage2-dev

Checking for dependency: DBus - Message bus system...
error: NOT FOUND! This is a REQUIRED dependency. Please make sure that this dependency is installed before installing or running HPLIP.
To install this dependency, execute this command:
sudo aptitude install --assume-yes libdbus-1-dev

Checking for dependency: gcc - GNU Project C and C++ Compiler...
OK, found.

Checking for dependency: GhostScript - PostScript and PDF language interpreter and previewer...
OK, found.

Checking for dependency: libcrypto - OpenSSL cryptographic library...
error: NOT FOUND! This is a REQUIRED dependency. Please make sure that this dependency is installed before installing or running HPLIP.
To install this dependency, execute this command:
sudo aptitude install --assume-yes openssl

Checking for dependency: libjpeg - JPEG library...
OK, found.

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

Checking for dependency: PolicyKit - Administrative policy framework...
warning: NOT FOUND! This is an OPTIONAL/RUNTIME ONLY dependency. Some HPLIP functionality may not function properly.
To install this dependency, execute this command:
sudo aptitude install --assume-yes policykit policykit-gnome

Checking for dependency: PyQt 4 DBus - DBus Support for PyQt4...
error: NOT FOUND! This is a REQUIRED/RUNTIME ONLY dependency. Please make sure that this dependency is installed before installing or running HPLIP.
To install this dependency, execute this command:
sudo aptitude install --assume-yes python-qt4-dbus

Checking for dependency: Python DBus - Python bindings for DBus...
OK, found.

Checking for dependency: Python devel - Python development files...
error: NOT FOUND! This is a REQUIRED/COMPILE TIME ONLY dependency. Please make sure that this dependency is installed before installing or running HPLIP.
To install this dependency, execute this command:
sudo aptitude install --assume-yes python-dev

Checking for dependency: Python libnotify - Python bindings for the libnotify Desktop notifications...
OK, found.

Checking for dependency: Python XML libraries...
OK, found.

Checking for dependency: Python 2.3 or greater - Required for fax functionality...
OK, found.

Checking for dependency: Python 2.2 or greater - Python programming language...
OK, found.

Checking for dependency: Reportlab - PDF library for Python...
warning: NOT FOUND! This is an OPTIONAL/RUNTIME ONLY dependency. Some HPLIP functionality may not function properly.
To install this dependency, execute this command:
sudo aptitude install --assume-yes python-reportlab

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
HPLIP 3.9.8 currently installed in '/usr/share/hplip'.

Current contents of '/etc/hp/hplip.conf' file:
# hplip.conf.  Generated from hplip.conf.in by configure.

[hplip]
version=3.9.8

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
internal-tag=3.9.8.36
restricted-build=no
ui-toolkit=qt4
qt3=no
qt4=yes
policy-kit=yes
hpijs-only-build=no
lite-build=no
udev-acl-rules=yes


Current contents of '/var/lib/hp/hplip.state' file:
[plugin]
eula = 1
installed = 1



Current contents of '~/.hplip/hplip.conf' file:
[last_used]
device_uri = hp:/usb/HP_LaserJet_1018?serial=xxxxxx(sniped)

[installation]
date_time = 10-01-04 11:33:50
version = 3.9.8.36



--------------------------
| DISCOVERED USB DEVICES |
--------------------------

  Device URI                               Model                  
  ---------------------------------------  -----------------------
  hp:/usb/HP_LaserJet_1018?serial=xxx(sniped)  HP LaserJet 1018       

---------------------------------
| INSTALLED CUPS PRINTER QUEUES |
---------------------------------

 
HP-LaserJet-1018
----------------
Type: Printer
Device URI: hp:/usb/HP_LaserJet_1018?serial=xxx(sniped)
PPD: /etc/cups/ppd/HP-LaserJet-1018.ppd
PPD Description: HP LaserJet 1018 Foomatic/foo2zjs (recommended)
Printer ready to printr HP-LaserJet-1018 is idle.  enabled since Mon 04 Jan 2010 11:29:40 AM MST

HP Linux Imaging and Printing System (ver. 3.9.8)
System Tray Status Service ver. 2.0

Copyright (c) 2001-9 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

warning: Qt/PyQt 4 initialization failed.
error: hp-systray requires Qt4 GUI and DBus support. Exiting.
warning: Unable to connect to dbus. Is hp-systray running?
Required plug-in status: Installed
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

HP Device 0x4117 at 001:007: 
    Device URI: hp:/usb/HP_LaserJet_1018?serial=xxx(sniped)

HP Linux Imaging and Printing System (ver. 3.9.8)
System Tray Status Service ver. 2.0

Copyright (c) 2001-9 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

warning: Qt/PyQt 4 initialization failed.
error: hp-systray requires Qt4 GUI and DBus support. Exiting.
warning: Unable to connect to dbus. Is hp-systray running?
    Device node: /dev/bus/usb/001/007
    Mode: 0660

---------------
| USER GROUPS |
---------------

xxxx adm dialout cdrom video plugdev lpadmin admin sambashare


-----------
| SUMMARY |
-----------

error: 15 errors and/or warnings.

Summary of needed commands to run to satisfy missing dependencies:
sudo aptitude install --assume-yes cupsddk cupsddk-drivers
sudo aptitude install --assume-yes libcupsys2-dev cupsys-bsd
sudo aptitude install --assume-yes libcupsimage2-dev
sudo aptitude install --assume-yes libdbus-1-dev
sudo aptitude install --assume-yes openssl
sudo aptitude install --assume-yes libsnmp-dev
sudo aptitude install --assume-yes libtool
sudo aptitude install --assume-yes libusb-dev
sudo aptitude install --assume-yes policykit policykit-gnome
sudo aptitude install --assume-yes python-qt4-dbus
sudo aptitude install --assume-yes python-dev
sudo aptitude install --assume-yes python-reportlab
sudo aptitude install --assume-yes libsane-dev

Please refer to the installation instructions at:
http://hplip.sourceforge.net/install/index.html


Done.
```There are a bunch of recommendations but maybe they will break Ubuntu since they are not Ubuntu developers...
 
On reread of this output I did install hp-systray.  I then used that to print a test page, again it said submitted and successful print but nothing came out.  Then I clicked "download firmware" via hp-systray and the printer did a reboot then I clicked print the test page... it printed.

Bug or just a printer specific quirk I don't know.

---

