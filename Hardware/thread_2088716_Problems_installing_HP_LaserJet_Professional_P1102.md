---
title: "Problems installing HP LaserJet Professional P1102w"
date: 2012-11-27
forum: Hardware
---

### Post by dedo86 on 2012-11-27
Hi all, I'm from Argentina, I'm new in this awesome world of linux, a couple of days installing the distro Ubuntu 12.04.1, and inform me after reading a lot about it. The point is that I'm trying to install an HP LaserJet Prefessional imrpesora P1102w, I looked everywhere and I can not find the solution.
Placing an hp-check and this is the result.

HP Linux Imaging and Printing System (ver. 3.12.2)
Dependency/Version Check Utility ver. 14.3

Copyright (c) 2011-14 Hewlett-Packard Development Company, LP
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
Linux diego-Inspiron-1525 3.2.0-33-generic-pae #52-Ubuntu SMP Thu Oct 18 16:39:21 UTC 2012 i686 i686 i386 GNU/Linux

Distribution:
ubuntu 12.04

Checking Python version...
OK, version 2.7.3 installed

Checking PyQt 4.x version...
error: NOT FOUND OR FAILED TO LOAD!

Checking for CUPS...
Status: el planificador de tareas se está ejecutando
warning: Version: (cups-config) Not available. Unable to determine installed version of CUPS.)
error_log is set to level: warn

Checking for dbus/python-dbus...
dbus daemon is running.
python-dbus version: 1.0.0


------------------------------------
| COMPILE AND RUNTIME DEPENDENCIES |
------------------------------------

note: To check for compile-time only dependencies, re-run hp-check with the -c parameter (ie, hp-check -c).
note: To check for run-time only dependencies, re-run hp-check with the -r parameter (ie, hp-check -r).

Checking for dependency: CUPS - Common Unix Printing System...
OK, found.

Checking for dependency: CUPS DDK - CUPS driver development kit...
warning: NOT FOUND! This is an OPTIONAL/RUNTIME ONLY dependency. Some HPLIP functionality may not function properly.

Checking for dependency: CUPS devel- Common Unix Printing System development files...
error: NOT FOUND! This is a REQUIRED/COMPILE TIME ONLY dependency. Please make sure that this dependency is installed before installing or running HPLIP.

Checking for dependency: CUPS image - CUPS image development files...
error: NOT FOUND! This is a REQUIRED/COMPILE TIME ONLY dependency. Please make sure that this dependency is installed before installing or running HPLIP.

Checking for dependency: DBus - Message bus system...
error: NOT FOUND! This is a REQUIRED dependency. Please make sure that this dependency is installed before installing or running HPLIP.

Checking for dependency: gcc - GNU Project C and C++ Compiler...
error: NOT FOUND! This is a REQUIRED/COMPILE TIME ONLY dependency. Please make sure that this dependency is installed before installing or running HPLIP.

Checking for dependency: GhostScript - PostScript and PDF language interpreter and previewer...
OK, found.

Checking for dependency: libcrypto - OpenSSL cryptographic library...
error: NOT FOUND! This is a REQUIRED dependency. Please make sure that this dependency is installed before installing or running HPLIP.

Checking for dependency: libjpeg - JPEG library...
error: NOT FOUND! This is a REQUIRED dependency. Please make sure that this dependency is installed before installing or running HPLIP.

Checking for dependency: libnetsnmp-devel - SNMP networking library development files...
error: NOT FOUND! This is a REQUIRED dependency. Please make sure that this dependency is installed before installing or running HPLIP.

Checking for dependency: libpthread - POSIX threads library...
OK, found.

Checking for dependency: libtool - Library building support services...
error: NOT FOUND! This is a REQUIRED/COMPILE TIME ONLY dependency. Please make sure that this dependency is installed before installing or running HPLIP.

Checking for dependency: libusb - USB library...
error: NOT FOUND! This is a REQUIRED dependency. Please make sure that this dependency is installed before installing or running HPLIP.

Checking for dependency: make - GNU make utility to maintain groups of programs...
OK, found.

Checking for dependency: PIL - Python Imaging Library (required for commandline scanning with hp-scan)...
OK, found.

Checking for dependency: PolicyKit - Administrative policy framework...
OK, found.

Checking for dependency: PyQt 4 DBus - DBus Support for PyQt4...
error: NOT FOUND! This is a REQUIRED/RUNTIME ONLY dependency. Please make sure that this dependency is installed before installing or running HPLIP.

Checking for dependency: Python DBus - Python bindings for DBus...
OK, found.

Checking for dependency: Python devel - Python development files...
error: NOT FOUND! This is a REQUIRED/COMPILE TIME ONLY dependency. Please make sure that this dependency is installed before installing or running HPLIP.

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
error: NOT FOUND! This is a REQUIRED/COMPILE TIME ONLY dependency. Please make sure that this dependency is installed before installing or running HPLIP.

Checking for dependency: scanimage - Shell scanning program...
OK, found.

Checking for dependency: xsane - Graphical scanner frontend for SANE...
warning: NOT FOUND! This is an OPTIONAL/RUNTIME ONLY dependency. Some HPLIP functionality may not function properly.


----------------------
| HPLIP INSTALLATION |
----------------------


Currently installed HPLIP version...
HPLIP 3.12.2 currently installed in '/usr/share/hplip'.

Current contents of '/etc/hp/hplip.conf' file:
# hplip.conf.  Generated from hplip.conf.in by configure.

[hplip]
version=3.12.2

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
internal-tag=3.12.2
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
[installation]
date_time = 27/11/12 09:22:01
version = 3.12.2

[last_used]
device_uri = hp:/net/HP_LaserJet_Professional_P1102w?zc=NPI4DC05A



--------------------------
| DISCOVERED USB DEVICES |
--------------------------

No devices found.

---------------------------------
| INSTALLED CUPS PRINTER QUEUES |
---------------------------------

 
Hewlett-Packard_HP_LaserJet_Professional_P1102w
-----------------------------------------------
Type: Unknown
Device URI: dnssd://HP%20LaserJet%20Professional%20P1102w._pdl-datastream._tcp.local/
PPD: /etc/cups/ppd/Hewlett-Packard_HP_LaserJet_Professional_P1102w.ppd
PPD Description: HP LaserJet Professional p1102w, hpcups 3.12.2, requires proprietary plugin
Printer status: la impresora Hewlett-Packard_HP_LaserJet_Professional_P1102w está inactiLista para imprimir.mar 27 nov 2012 09:19:20 ART
warning: Printer is not HPLIP installed. Printers must use the hp: or hpfax: CUPS backend to function in HPLIP.

HP-LaserJet-Professional-P1102w
-------------------------------
Type: Printer
Device URI: hp:/usb/HP_LaserJet_Professional_P1102w?serial=000000000RK00BG7PR1a
PPD: /etc/cups/ppd/HP-LaserJet-Professional-P1102w.ppd
PPD Description: HP LaserJet Pro P1102w Foomatic/foo2zjs-z2 (recommended)
Printer status: la impresora HP-LaserJet-Professional-P1102w está deshabilitada desde maUnplugged or turned offART -

HP Linux Imaging and Printing System (ver. 3.12.2)
System Tray Status Service ver. 2.0

Copyright (c) 2001-9 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

warning: Qt/PyQt 4 initialization failed.
error: hp-systray requires Qt4 GUI and DBus support. Exiting.
warning: Unable to connect to dbus. Is hp-systray running?
error: Required plug-in status: Not installed
error: Unable to communicate with device (code=12): hp:/usb/HP_LaserJet_Professional_P1102w?serial=000000000RK00BG7PR1a
error: Device not found
error: Communication status: Failed


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


 
---------------
| USER GROUPS |
---------------

diego adm cdrom sudo dip plugdev lpadmin sambashare

error: User needs to be member of group 'lp' to enable print, scan & fax.
User member of group 'lpadmin'.

-----------
| SUMMARY |
-----------

error: 18 errors and/or warnings.

Please refer to the installation instructions at:
[http://hplip.sourceforge.net/install/index.html](http://hplip.sourceforge.net/install/index.html)

Thanks for help..

---

### Post by Bucky Ball on 2012-11-27
How are you trying to communicate with this printer? Wired, wirelessly, USB, on a LAN? ;)

---

### Post by dedo86 on 2012-11-27
HI Bucky Ball, i'm trying to communicate with wirelles.

---

### Post by Bucky Ball on 2012-11-27
Cool. You need to find out the IP address of your printer. Not sure with HP but generally you press a button a few times and an information sheet pops out with all details. The IP should be there.

Then go to 'Printing' in Ubuntu and Add Printer. Click 'Find Network Printer' and give it some time to find. Once you're there, it's found the right printer, you can select a driver and use the IP address to get rolling. 

You need HPLip installed to get it happening and you have that. HP are well supported. )

---

### Post by dedo86 on 2012-11-27
For USB works well just print a test page. But I would also set it to print by Wirelles.

---

### Post by kurt18947 on 2012-11-27
Do you have HPLIP installed?  I use synaptic as a package manager and when I enter "hplip" in the search box a number of related entries come up.  HP printers are usually pretty easy.  Here's a personal prejudice re wireless printing.  If you're given a choice of network protocols, I prefer JetDirect/socket:.  I've had problems with others not recognizing my Brother printers when shutting down and restarting.  Using that though, you do have to assign a static I.P. address to the printer.  You're telling the P.C. to send print jobs to a specific I.P. address.  The I.P. address of the printer needs to be static.

---

### Post by dedo86 on 2012-11-27
Thank you very much for the reply, now I will assign a fixed IP to the printer and I will try.

Now using USB long me the following error / usr / lib / cups / backend / hp failed

And when you start ubuntu the following message:

hplip service status
no system tray detected on This System. Unable to start exiting

And I do not recognize the printer, I see this in CUPS

---

