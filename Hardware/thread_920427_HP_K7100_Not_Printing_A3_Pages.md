---
title: "HP K7100 Not Printing A3 Pages"
date: 2008-09-15
forum: Hardware
---

### Post by actionmarker on 2008-09-15
I have just recently installed my HP OfficeJet K7100 printer. All works perfectly except I cannot select A3. It is not an option. 

I am running Ubuntu 8.04, HPLIP 2.8.7.

Is there another driver I can set the printer to that supports A3?

Thanks
am

---

### Post by Sef on 2008-09-15
Applications > Accessories > Terminal

Then paste or type this command:

```
hp-check -t
```

---

### Post by actionmarker on 2008-09-15
Thanks for that.

I ran the script as you suggested.

See below for details.

I tried printing again and still have no A3 selection, so I created a custom size.

It printed the text as if it were printing A3 (text size), but cut off the print at the normal borders of an A4 page

A test print does the same, with the A3 paper feeding normally, but it only covers the page to A4 size.

Any other suggestions would be greatly appreciated.

Thanks
am

__________________________________________________________________
hp-check -t

HP Linux Imaging and Printing System (ver. 2.8.7)
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
Linux petercowle-laptop 2.6.24-19-generic #1 SMP Wed Aug 20 22:56:21 UTC 2008 i686 GNU/Linux

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

Checking for dependency: PyQt - Qt interface for Python...
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
HPLIP 2.8.7 currently installed in '/usr/share/hplip'.

Current contents of '/etc/hp/hplip.conf' file:
# hplip.conf.  Generated from hplip.conf.in by configure.

[hplip]
version=2.8.7

[dirs]
home=/usr/share/hplip
run=/var/run
ppd=/usr/share/ppd/hpijs/HP
ppdbase=/usr/share/ppd/hpijs
doc=/usr/share/doc/hplip-2.8.7
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
internal-tag=2.8.7.4
restricted-build=no



--------------------------
| DISCOVERED USB DEVICES |
--------------------------

  Device URI                        Model                        
  --------------------------------  -----------------------------
  hp:/usb/hp_color_LaserJet_2550_s  HP color LaserJet 2550 series
  eries?serial=00CNHGC47898                                      
  hp:/usb/Officejet_K7100?serial=M  HP Officejet K7100           
  Y7A31111W051S                                                  

---------------------------------
| INSTALLED CUPS PRINTER QUEUES |
---------------------------------

 
hp_color_LaserJet_2550_series
-----------------------------
Type: Printer
Installed in HPLIP?: Yes, using the hp: CUPS backend.
Device URI: hp:/usb/hp_color_LaserJet_2550_series?serial=00CNHGC47898
PPD: /etc/cups/ppd/hp_color_LaserJet_2550_series.ppd
PPD Description: HP Color LaserJet 2550 Series Postscript (recommended)
Printer status: printer hp_color_LaserJet_2550_series is idle.  enabled since Mon 15 Sep 2008 22:39:56 EST
Communication status: Good

i560
----
Type: Unknown
Installed in HPLIP?: No, not using the hp: or hpfax: CUPS backend.
Device URI: usb://Canon/i560
PPD: /etc/cups/ppd/i560.ppd
PPD Description: Canon i560 - CUPS+Gutenprint v5.0.2 Simplified
Printer status: printer i560 is idle.  enabled since Thu 11 Sep 2008 07:07:17 EST
warning: Printer is not HPLIP installed. Printers must use the hp: or hpfax: CUPS backend to function in HPLIP.
Officejet_K7100
---------------
Type: Printer
Installed in HPLIP?: Yes, using the hp: CUPS backend.
Device URI: hp:/usb/Officejet_K7100?serial=MY7A31111W051S
PPD: /etc/cups/ppd/Officejet_K7100.ppd
PPD Description: HP Officejet k7100 Foomatic/hpijs, hpijs 2.8.7
Printer status: printer Officejet_K7100 is idle.  enabled since Mon 15 Sep 2008 22:39:56 EST
Communication status: Good

PDF
---
Type: Unknown
Installed in HPLIP?: No, not using the hp: or hpfax: CUPS backend.
Device URI: cups-pdf:/
PPD: /etc/cups/ppd/PDF.ppd
PPD Description: Generic PDF file generator
Printer status: printer PDF is idle.  enabled since Wed 02 Jul 2008 20:22:03 EST
warning: Printer is not HPLIP installed. Printers must use the hp: or hpfax: CUPS backend to function in HPLIP.

----------------------
| SANE CONFIGURATION |
----------------------

'hpaio' in '/etc/sane.d/dll.conf'...
OK, found. SANE backend 'hpaio' is properly set up.

Checking output of 'scanimage -L'...
device `plustek:libusb:005:005' is a Canon CanoScan LiDE25 flatbed scanner


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
 
HP Device 0x2612 at 005:007: 
    Device URI: hp:/usb/Officejet_K7100?serial=MY7A31111W051S
    Device node: /dev/bus/usb/005/007
    Mode: 0666
getfacl: Removing leading '/' from absolute path names
# file: dev/bus/usb/005/007
# owner: root
# group: lp
user::rw-
group::rw-
other::rw-



HP Device 0x1c17 at 005:006: 
    Device URI: hp:/usb/hp_color_LaserJet_2550_series?serial=00CNHGC47898
    Device node: /dev/bus/usb/005/006
    Mode: 0666
getfacl: Removing leading '/' from absolute path names
# file: dev/bus/usb/005/006
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
[http://hplip.sourceforge.net/install/index.html](http://hplip.sourceforge.net/install/index.html)


Done.
______________________________________________________

---

### Post by actionmarker on 2008-09-22
Since my last post,

I tried changing the driver to a different A3 printer HP Deskjet 9800.
No change.

Looking at the HPLIP site, what is the HPIJS driver. 
I found the list of paper sizes available and A3 is happily in the list.
See [http://hplip.sourceforge.net/tech_docs/page_sizes.html](http://hplip.sourceforge.net/tech_docs/page_sizes.html)  
How does HPIJS differ to the HPLIP?

Thanks
am

---

### Post by Sef on 2008-09-22
> How does HPIJS differ to the HPLIP?

Here's the answer from [HPLIP FAQ]("http://hplip.sourceforge.net/faqs.html"): 

> **Question: What is included with HPLIP?**
 Answer:
 
[LIST=1]
[*]HPLIP is a complete imaging and printing system for CUPS that includes HPIJS.
[*]HPIJS is the basic printing driver that supports printing from CUPS, LPD, PPR, and other spoolers.
[/LIST]


---

### Post by actionmarker on 2008-09-26
Solution Found!

I found on another forum the same issue being described.

See link:
[http://forums.fedoraforum.org/showthread.php?t=184733](http://forums.fedoraforum.org/showthread.php?t=184733)

It turns out that the ppd file in hplip does not have the A3 paper size in the text.

Bit slack by HP as its an A3 printer!

I added the lines into my ppd file, pointed the printer driver to that file and all is working perfectly.

Thanks Sef for pointing me in the right direction.
There is always a solution to every problem.

am

---

