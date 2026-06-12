---
title: "HP OfficeJet G95 not printing"
date: 2011-06-14
forum: Hardware
---

### Post by turncoat on 2011-06-14
ubuntu 11.04
cups 1.4.6
hplip 3.11.1
printer [http://hplipopensource.com/hplip-web/models/officejet/officejet_g95.html](http://hplipopensource.com/hplip-web/models/officejet/officejet_g95.html)

The printer is connected via USB and it works fine on Windows XP.

On ubuntu, when I attempt to print a test page using the GUI it chages status from Idle to Processing and then to "Idle - /usr/lib/cups/backend/hp failed"

Every job gets these errors in the log:

> D [14/Jun/2011:14:07:01 +0200] [Job 32] prnt/backend/hp.c 768: ERROR: cannot open channel PRINT
D [14/Jun/2011:14:07:01 +0200] [Job 32] GPL Ghostscript 9.01: Unrecoverable error, exit code 1
D [14/Jun/2011:14:07:01 +0200] PID 3137 (/usr/lib/cups/backend/hp) stopped with status 1!
D [14/Jun/2011:14:07:01 +0200] [Job 32] renderer exited with status 1
D [14/Jun/2011:14:07:01 +0200] [Job 32] Possible error on renderer command line or PostScript error. Check options.Kid3 exit status: 3
D [14/Jun/2011:14:07:01 +0200] PID 3136 (/usr/lib/cups/filter/foomatic-rip) stopped with status 9!
I [14/Jun/2011:14:07:01 +0200] [Job 32] Backend returned status 1 (failed)hp-check -r returns this:
```

---------------
| SYSTEM INFO |
---------------

Basic system information:
Linux {username}-desktop 2.6.35-28-generic #50-Ubuntu SMP Fri Mar 18 18:42:20 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

Distribution:
ubuntu 11.04

Checking Python version...
OK, version 2.7.1 installed

Checking PyQt 4.x version...
OK, version 4.8.3 installed.

Checking for CUPS...
Status: scheduler is running
warning: Version: (cups-config) Not available. Unable to determine installed version of CUPS.)
error_log is set to level: debug

Checking for dbus/python-dbus...
dbus daemon is running.
python-dbus version: 0.83.1


------------------------
| RUNTIME DEPENDENCIES |
------------------------


Checking for dependency: CUPS - Common Unix Printing System...
OK, found.

Checking for dependency: CUPS DDK - CUPS driver development kit...
warning: NOT FOUND! This is an OPTIONAL/RUNTIME ONLY dependency. Some HPLIP functionality may not function properly.

Checking for dependency: GhostScript - PostScript and PDF language interpreter and previewer...
OK, found.

Checking for dependency: PIL - Python Imaging Library (required for commandline scanning with hp-scan)...
OK, found.

Checking for dependency: PolicyKit - Administrative policy framework...
OK, found.

Checking for dependency: PyQt 4 DBus - DBus Support for PyQt4...
OK, found.

Checking for dependency: Python DBus - Python bindings for DBus...
OK, found.

Checking for dependency: Python libnotify - Python bindings for the libnotify Desktop notifications...
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
HPLIP 3.11.1 currently installed in '/usr/share/hplip'.

Current contents of '/etc/hp/hplip.conf' file:
# hplip.conf.  Generated from hplip.conf.in by configure.

[hplip]
version=3.11.1

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
internal-tag=3.11.1.19
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
date_time = 06/14/2011 15:00:22
version = 3.11.1.19

[settings]
systray_visible = 0
systray_messages = 0

[last_used]
device_uri = 
printer_name = 
working_dir = .

[commands]
scan = /usr/bin/simple-scan %SANE_URI%

[refresh]
rate = 30
enable = false
type = 1

[polling]
enable = false
interval = 5
device_list = 

[fax]
voice_phone = 
email_address = 



--------------------------
| DISCOVERED USB DEVICES |
--------------------------

  Device URI                        Model           
  --------------------------------  ----------------
  hp:/usb/OfficeJet_G95?serial=SGG  HP OfficeJet G95
  14E3521VL                                         

---------------------------------
| INSTALLED CUPS PRINTER QUEUES |
---------------------------------

 
OfficeJet_G95
-------------
Type: Printer
Device URI: hp:/usb/OfficeJet_G95?serial=SGG14E3521VL
PPD: /etc/cups/ppd/OfficeJet_G95.ppd
PPD Description: HP Officejet g95 hpijs, 3.11.1
Printer status: printer OfficeJet_G95 is idle.  enabled since Tue 14 Jun 2011 02:32:59 P/usr/lib/cups/backend/hp failed

HP Linux Imaging and Printing System (ver. 3.11.1)
System Tray Status Service ver. 2.0

Copyright (c) 2001-9 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

Communication status: Good

OfficeJet_G95_fax
-----------------
Type: Fax
Device URI: hpfax:/usb/OfficeJet_G95?serial=SGG14E3521VL
PPD: /etc/cups/ppd/OfficeJet_G95_fax.ppd
PPD Description: HP Fax hpcups
Printer status: printer OfficeJet_G95_fax is idle.  enabled since Tue 14 Jun 2011 01:25:16 PM CEST
Communication status: Good


----------------------
| SANE CONFIGURATION |
----------------------

'hpaio' in '/etc/sane.d/dll.conf'...
'hpaio' in '/etc/sane.d/dll.d/hplip'...
OK, found. SANE backend 'hpaio' is properly set up.

Checking output of 'scanimage -L'...
\/usr/lib/pymodules/python2.7/gtk-2.0/gtk/__init__.py:127: RuntimeWarning: PyOS_InputHook is not available for interactive use of PyGTK
  set_interactive(1)
device `hpaio:/usb/OfficeJet_G95?serial=SGG14E3521VL' is a Hewlett-Packard OfficeJet_G95 all-in-one


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

HP Device 0x411 at 002:002: 
    Device URI: hp:/usb/OfficeJet_G95?serial=SGG14E3521VL
    Device node: /dev/bus/usb/002/002
    Mode: 0664

---------------
| USER GROUPS |
---------------

{username} adm lp dialout cdrom plugdev lpadmin admin sambashare

User member of group 'lp'. Enables print/ scan/ fax.
User member of group 'lpadmin'.

-----------
| SUMMARY |
-----------

error: 1 error or warning.

Please refer to the installation instructions at:
http://hplip.sourceforge.net/install/index.html


Done.



```Does anyone know what's wrong?
Thanks in advance.

---

