---
title: "HP 1280 Not Printing A3 Pages"
date: 2008-10-23
forum: General Help
---

### Post by CanonKen on 2008-10-23
Anyone any ideas? try printing A3 and it just prints it at A4 size

```
ken@ken:~$ hp-check -t

HP Linux Imaging and Printing System (ver. 2.8.9)
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
 
---------------
| SYSTEM INFO |
---------------

Basic system information:
Linux ken 2.6.24-16-generic #1 SMP Thu Apr 10 13:23:42 UTC 2008 i686 GNU/Linux

Distribution:
ubuntu 8.04

HPOJ running?
No, HPOJ is not running (OK).

Checking Python version...
OK, version 2.5.2 installed

Checking PyQt version...
OK, version 3.17 installed.

Checking SIP version...
error: SIP not installed or version not found.

Checking for CUPS...
Status: scheduler is running
Version: 1.3.7
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

Checking for dependency: PyQt 3- Qt interface for Python (for Qt version 3.x)...
OK, found.

Checking for dependency: PyQt 4- Qt interface for Python (for Qt version 4.x)...
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
HPLIP 2.8.9 currently installed in '/usr/share/hplip'.

Current contents of '/etc/hp/hplip.conf' file:
# hplip.conf.  Generated from hplip.conf.in by configure.

[hplip]
version=2.8.9

[dirs]
home=/usr/share/hplip
run=/var/run
ppd=/usr/share/ppd/hpijs/HP
ppdbase=/usr/share/ppd/hpijs
doc=/usr/share/doc/hplip-2.8.9
icon=/usr/share/applications
cupsbackend=/usr/lib/cups/backend
cupsfilter=/usr/lib/cups/filter
drv=/usr/share/cups/drv/hp/

# Following values are determined at configure time and cannot be changed.
[configure]
network-build=yes
pp-build=no
gui-build=yes
scanner-build=yes
fax-build=yes
dbus-build=yes
cups11-build=no
doc-build=yes
shadow-build=no
foomatic-drv-install=yes
foomatic-ppd-install=no
foomatic-rip-hplip-install=yes
internal-tag=2.8.9.0
restricted-build=no
ui-toolkit=qt3



--------------------------
| DISCOVERED USB DEVICES |
--------------------------

  Device URI                        Model           
  --------------------------------  ----------------
  hp:/usb/Deskjet_1280?serial=CN59  HP Deskjet 1280 
  6J50B3UP                                          

---------------------------------
| INSTALLED CUPS PRINTER QUEUES |
---------------------------------

 
Deskjet_1280
------------
Type: Printer
Installed in HPLIP?: Yes, using the hp: CUPS backend.
Device URI: hp:/usb/Deskjet_1280?serial=CN596J50B3UP
PPD: /etc/cups/ppd/Deskjet_1280.ppd
PPD Description: HP Deskjet 1280 Foomatic/hpijs, hpijs 2.8.2
Printer status: printer Deskjet_1280 is idle.  enabled since Thu 23 Oct 2008 19:03:47 BST
Communication status: Good

Deskjet_1280_2
--------------
Type: Printer
Installed in HPLIP?: Yes, using the hp: CUPS backend.
Device URI: hp:/usb/Deskjet_1280?serial=CN596J50B3UP
PPD: /etc/cups/ppd/Deskjet_1280_2.ppd
PPD Description: HP Deskjet 1280 Foomatic/hpijs, hpijs 2.8.9
Printer status: printer Deskjet_1280_2 is idle.  enabled since Thu 23 Oct 2008 22:53:22 BST
Communication status: Good

PDF
---
Type: Unknown
Installed in HPLIP?: No, not using the hp: or hpfax: CUPS backend.
Device URI: cups-pdf:/
PPD: /etc/cups/ppd/PDF.ppd
PPD Description: Generic PDF file generator
Printer status: printer PDF is idle.  enabled since Wed 04 Jun 2008 20:17:24 BST
warning: Printer is not HPLIP installed. Printers must use the hp: or hpfax: CUPS backend to function in HPLIP.
Stylus_Photo_R300
-----------------
Type: Unknown
Installed in HPLIP?: No, not using the hp: or hpfax: CUPS backend.
Device URI: epson:/dev/usb/lp0
PPD: /etc/cups/ppd/Stylus_Photo_R300.ppd
PPD Description: Epson Stylus Photo R300 - CUPS+Gutenprint v5.0.2 Simplified
Printer status: printer Stylus_Photo_R300 is idle.  enabled since Wed 04 Jun 2008 21:19:36 BST
warning: Printer is not HPLIP installed. Printers must use the hp: or hpfax: CUPS backend to function in HPLIP.

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
 
HP Device 0x1412 at 002:005: 
    Device URI: hp:/usb/Deskjet_1280?serial=CN596J50B3UP
    Device node: /dev/bus/usb/002/005
    Mode: 0666
getfacl: Removing leading '/' from absolute path names
# file: dev/bus/usb/002/005
# owner: root
# group: lp
user::rw-
group::rw-
other::rw-



-----------
| SUMMARY |
-----------

error: 3 errors and/or warnings.

Please refer to the installation instructions at:
http://hplip.sourceforge.net/install/index.html


Done.
ken@ken:~$ 

```

---

### Post by Iowan on 2008-10-23
I had a similar problem: [http://ubuntuforums.org/showthread.php?t=285444]("http://ubuntuforums.org/showthread.php?t=285444")
In brief, change */etc/papersize*.

---

### Post by CanonKen on 2008-10-24
Thanks, I'll give it a try and see what happens, why letter rthough and not A3??

---

### Post by CanonKen on 2008-10-24
No joy, still printing at A4 size,got 3 installs now for this printer, how do i uninstall all of them and start from scratch

---

### Post by matey3 on 2008-10-24
> **CanonKen said:**
> No joy, still printing at A4 size,got 3 installs now for this printer, how do i uninstall all of them and start from scratch
Is this a command line printing?
can you get into the printer itself? some have access panel some can be telnet-ed to.
I had the same problem with xerox but I did change the configurations in GUI (printer properties)

---

### Post by CanonKen on 2008-10-24
I've tried changing the properties to A3, Ledger, Letter and super B and they all print at A4.
Tried both photos and a spreadsheet, they both print A4, I have just printed a page off Firefox though and that printed at A3 :confused: doing my head in :)

---

### Post by CanonKen on 2008-10-24
Well I don't know what i've done but its working in Gimp :confused:
Deleted all the printers, re-installed, re-started, now it works :)
Still won't print a spreadsheet at A3 though

---

