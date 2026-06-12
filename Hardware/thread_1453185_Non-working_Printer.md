---
title: "Non-working Printer"
date: 2010-04-12
forum: Hardware
---

### Post by lawdog on 2010-04-12
After reading all the posts regarding printer problems after upgrading to Karmic Koala, I regretfully post the following:

Upgraded to 9.10 on Saturday.
Attached USB printer is HP Laserjet 1020
HP Device Manager set up the printer for me, and a test page was able to print.
Next day, and ever since, it does not print at all.

I continually have the following error message when I view printer properties:

> Filter directory "/usr/lib/cups/filter" for printer "HP_LaserJet_1020" has insecure permissions (040777)

Actions taken with problem still occurring:
Have installed latest hplip version (3.10.2)
Have deleted the printer dozens to times and re-added
Have followed all steps on the hplip troubleshooting page
Have installed required plugin from hplip
Firmware download errors out and won't complete

Running hp-check yields the following:

> ---------------
| SYSTEM INFO |
---------------

Basic system information:
Linux jonathan-desktop 2.6.31-21-generic #59-Ubuntu SMP Wed Mar 24 07:28:56 UTC 2010 i686 GNU/Linux

Distribution:
ubuntu 9.10

Checking Python version...
OK, version 2.6.4 installed

Checking PyQt 4.x version...
OK, version 4.6 installed.

Checking for CUPS...
Status: scheduler is running
Version: 1.4.1
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
# hplip.conf.  Generated from hplip.conf.in by configure.

[hplip]
version=3.10.2

[dirs]
home=/usr/share/hplip
run=/var/run
ppd=/usr/share/ppd/HP
ppdbase=/usr/share/ppd
doc=/usr/share/doc/hplip-3.10.2
icon=/usr/share/applications
cupsbackend=/usr/lib/cups/backend
cupsfilter=/usr/lib/cups/filter
drv=/usr/share/cups/drv/hp

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
hpijs-install=no
foomatic-drv-install=no
foomatic-ppd-install=no
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
[plugin]
eula = 1
installed = 1



Current contents of '~/.hplip/hplip.conf' file:
[last_used]
printer_name=HP_LaserJet_1020_2
working_dir=.
device_uri="hp:/usb/HP_LaserJet_1020?serial=JL2QR40"

[commands]
scan=/usr/bin/xsane -V %SANE_URI%

[installation]
version=3.10.2
date_time=04/11/2010 23:37:16

[settings]
systray_messages=0
systray_visible=0

[fax]
email_address=
voice_phone=

[refresh]
rate=30
enable=false
type=1

[polling]
enable=false
device_list=
interval=5


--------------------------
| DISCOVERED USB DEVICES |
--------------------------

  Device URI                        Model           
  --------------------------------  ----------------
  hp:/usb/HP_LaserJet_1020?serial=  HP LaserJet 1020
  JL2QR40                                           

---------------------------------
| INSTALLED CUPS PRINTER QUEUES |
---------------------------------

 
HP_LaserJet_1020
----------------
Type: Printer
Device URI: hp:/usb/HP_LaserJet_1020?serial=JL2QR40
PPD: /etc/cups/ppd/HP_LaserJet_1020.ppd
PPD Description: HP LaserJet 1020, hpcups 3.10.2, requires proprietary plugin
Printer status: printer HP_LaserJet_1020 is idle.  enabled since Mon 12 Apr 2010 10:19:0Filter directory "/usr/lib/cups/filter" for printer "HP_LaserJet_1020" has insecure permissions (040777)
Required plug-in status: Installed
Communication status: Good


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

HP Device 0x2b17 at 001:002: 
    Device URI: hp:/usb/HP_LaserJet_1020?serial=JL2QR40
    Device node: /dev/bus/usb/001/002
    Mode: 0660
getfacl: Removing leading '/' from absolute path names
# file: dev/bus/usb/001/002
# owner: root
# group: lp
user::rw-
user:jonathan:rw-
group::rw-
mask::rw-
other::---



---------------
| USER GROUPS |
---------------

root


-----------
| SUMMARY |
-----------

No errors or warnings.


I'm just banging my head against the wall with this.  I've been working on finding a solution for nearly seven hours all together.  Any help will be much appreciated.

---

### Post by pascalacer on 2010-04-13
[FONT=Trebuchet MS]Hi

you could try this set of command: 

sudo chown -hR root /usr/lib/cups/filter
sudo chown -hR root /usr/lib/cups/backend
sudo chgrp -hR root /usr/lib/cups/filter
sudo chgrp -hR root /usr/lib/cups/backend

it worked for me...
[/FONT]

---

### Post by lawdog on 2010-04-13
> **pascalacer said:**
> [FONT=Trebuchet MS]Hi

you could try this set of command: 

sudo chown -hR root /usr/lib/cups/filter
sudo chown -hR root /usr/lib/cups/backend
sudo chgrp -hR root /usr/lib/cups/filter
sudo chgrp -hR root /usr/lib/cups/backend

it worked for me...
[/FONT]

Thank you for the suggestion.

I tried this after you posted it.  The result is that now the system will not even recognize that the printer is there!

I have tried restarting twice, and running hp-setup AND adding a printer in the administration tab, and in both instances, the printer is not found.  I even plugged into another USB port before the last restart, and it still won't find it.

And yes, it's plugged in and turned on. :)

Aaaargh!  This is so frustrating!


I would also add that the printer works fine when using XP (dual boot), so it's definitely an Ubuntu problem.

---

### Post by pascalacer on 2010-04-14
it's getting nasty... you did run again hp-check?

---

### Post by lawdog on 2010-04-14
After several restarts, deleting the printer in Sys -> Admin -> Printing, and reloading the printer and running hp -setup numerous times, I got it to recognize the printer again.

That is until I started the computer today from shutdown.
Now, hp-check looks like this:

```
HP Linux Imaging and Printing System (ver. 3.10.2)
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
Linux jonathan-desktop 2.6.31-21-generic #59-Ubuntu SMP Wed Mar 24 07:28:56 UTC 2010 i686 GNU/Linux

Distribution:
ubuntu 9.10

Checking Python version...
OK, version 2.6.4 installed

Checking PyQt 4.x version...
OK, version 4.6 installed.

Checking for CUPS...
Status: scheduler is running
Version: 1.4.1
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
# hplip.conf.  Generated from hplip.conf.in by configure.

[hplip]
version=3.10.2

[dirs]
home=/usr/share/hplip
run=/var/run
ppd=/usr/share/ppd/HP
ppdbase=/usr/share/ppd
doc=/usr/share/doc/hplip-3.10.2
icon=/usr/share/applications
cupsbackend=/usr/lib/cups/backend
cupsfilter=/usr/lib/cups/filter
drv=/usr/share/cups/drv/hp

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
hpijs-install=no
foomatic-drv-install=no
foomatic-ppd-install=no
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
[plugin]
eula = 1
installed = 1



Current contents of '~/.hplip/hplip.conf' file:
[last_used]
printer_name = HP_LaserJet_1020_2
working_dir = .
device_uri = "hp:/usb/HP_LaserJet_1020?serial=JL2QR40"

[commands]
scan = /usr/bin/xsane -V %SANE_URI%

[installation]
version = 3.10.2rc1.9
date_time = 04/14/2010 14:41:26

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

No devices found.

---------------------------------
| INSTALLED CUPS PRINTER QUEUES |
---------------------------------

 
HP_LaserJet_1020
----------------
Type: Printer
Device URI: hp:/usb/HP_LaserJet_1020?serial=JL2QR40
PPD: /etc/cups/ppd/HP_LaserJet_1020.ppd
PPD Description: HP LaserJet 1020, hpcups 3.10.2, requires proprietary plugin
Printer status: printer HP_LaserJet_1020 is idle.  enabled since Tue 13 Apr 2010 10:57:0Filter directory "/usr/lib/cups/filter" for printer "HP_LaserJet_1020" has insecure permissions (040777)
Required plug-in status: Installed
error: Unable to communicate with device (code=12): hp:/usb/HP_LaserJet_1020?serial=JL2QR40
error: Device not found
error: Communication status: Failed


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

HP Device 0x2b17 at 001:003: 
warning:     Device URI: (Makeuri FAILED)

---------------
| USER GROUPS |
---------------

jonathan adm lp dialout cdrom floppy audio dip video plugdev fuse lpadmin admin


-----------
| SUMMARY |
-----------

error: 1 error or warning.

Please refer to the installation instructions at:
http://hplip.sourceforge.net/install/index.html


Done.

```


So that's fun: Some new errors!  

Seriously, it shouldn't be this complicated just to add a USB printer.

Should also add that the printer was turned on and connected BEFORE startup, as has been my custom since upgrading to Jaunty because it will not recognize my printer if I switch it on AFTER startup.  Had hoped this problem would've been solved in the new upgrade.

---

### Post by lawdog on 2010-04-21
Still need some help on this issue.  Very hard to get by without a printer.  Anyone?

---

### Post by richard650 on 2010-05-02
I have a similar issue with 10.04 and invested quite some time trying to solve it. no success. 

any help would be truly appreciated.

Richard


==============================================

Ubuntu 10.04, HP LaserJet 1020 not printing

Note: solutions to this problem under Ubuntu 9.04
did not solve the problem.


Platform:
OptiPlex 755, Dell Inc. Intel(R) Core(TM)2 Duo 
CPU E8500 @3.16GHz. 4GB Mem. NVIDIA GeForce 9500 GT.

OS:
Linux andromeda 2.6.32-21-generic #32-Ubuntu SMP i686 GNU/Linux
Ubuntu 10.04 LTS, lucid 


*********************
Problem: after various attempts to install HP LaserJet 1020
under Ubuntu 10.04, no printing. installation seems OK,
printer is added, but no communication.

(1) drivers provided by Ubuntu 10.04 did install printer,
but printing did not work.

(2) could not install hplip with functional GUI using Ubuntu hplip 
packages 3.10.2 or automatic hplip-3.10.2.run due to errors
/wrt Qt4 dbus support, although all required qt4 packages
are installed.

(3) finally built hplip manually for Ubuntu 10.04. 

see:
[http://hplipopensource.com/hplip-web/install/manual/distros/ubuntu.html](http://hplipopensource.com/hplip-web/install/manual/distros/ubuntu.html)

with this, the GUI works.


PLUGIN/PRINTER ERRORS:


***********************************
hp-setup seems OK. but hp-firmware fails:

Firmware download to device failed.
hp:/usb/HP_LaserJet_1020?serial=JL2DP9V

however, firmware exists:

$ ls /usr/share/hplip/data/firmware/
hp_laserjet_1020.fw.gz
...


$sudo hp-plugin -i

gives:

...

Downloading firmware to device hp:/usb/HP_LaserJet_1020?serial=JL2DP9V...
error: Channel write error
error: An error occured: Device I/O error

***********************************
hplip:
HPLIP Device Status
HP_LaserJet_1020 (JL2DP9V)
Unknown error (1018
***********************************
xsane 0.996 after plugging in printer:
no devices available
***********************************

here are device permissions.

$ ll /dev/usb/lp0 
0 crw-rw-rw- 1 root lp 180, 0 2010-05-02 08:22 /dev/usb/lp0


also added root and user to lp group

$ id -Gn lp
lp root richard


hp-check log is below. any help would be truly appreciated.

Richard


==============================================
================== hp-check ====================
==============================================
after sending test page:

$ sudo hp-check



hp-check[3317]: info: :
Initializing. Please wait...
Ubuntu

10.04

scheduler is running

1.4.3

Linux andromeda 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 i686 GNU/Linux

hp-check[3317]: info: :
hp-check[3317]: info: :---------------
hp-check[3317]: info:  SYSTEM INFO |
hp-check[3317]: info: :---------------
hp-check[3317]: info: :
hp-check[3317]: info: :[01mBasic system information:[0m
hp-check[3317]: info: :Linux andromeda 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 i686 GNU/Linux
hp-check[3317]: info: :
hp-check[3317]: info: :[01mDistribution:[0m
hp-check[3317]: info: :ubuntu 10.04
hp-check[3317]: info: :
hp-check[3317]: info: :[01mChecking Python version...[0m
hp-check[3317]: info: :OK, version 2.6.5 installed
hp-check[3317]: info: :
hp-check[3317]: info: :[01mChecking PyQt 4.x version...[0m
hp-check[3317]: info: :OK, version 4.7.2 installed.
hp-check[3317]: info: :
hp-check[3317]: info: :[01mChecking for CUPS...[0m
hp-check[3317]: info: :Status: scheduler is running
hp-check[3317]: info: :Version: 1.4.3
hp-check[3317]: info: :error_log is set to level: warn
hp-check[3317]: info: :
hp-check[3317]: info: :[01mChecking for dbus/python-dbus...[0m
hp-check[3317]: info: :dbus daemon is running.
hp-check[3317]: info: ython-dbus version: 0.83.0
hp-check[3317]: info: :
hp-check[3317]: info: :
hp-check[3317]: info: :------------------------------------
hp-check[3317]: info: COMPILE AND RUNTIME DEPENDENCIES |
hp-check[3317]: info: :------------------------------------
hp-check[3317]: info: :
note: To check for compile-time only dependencies, re-run hp-check with the -c parameter (ie, hp-check -c).
note: To check for run-time only dependencies, re-run hp-check with the -r parameter (ie, hp-check -r).
hp-check[3317]: info: :
hp-check[3317]: info: :[01mChecking for dependency: CUPS - Common Unix Printing System...[0m
hp-check[3317]: info: :OK, found.
hp-check[3317]: info: :
hp-check[3317]: info: :[01mChecking for dependency: CUPS devel- Common Unix Printing System development files...[0m
hp-check[3317]: info: :OK, found.
hp-check[3317]: info: :
hp-check[3317]: info: :[01mChecking for dependency: CUPS image - CUPS image development files...[0m
hp-check[3317]: info: :OK, found.
hp-check[3317]: info: :
hp-check[3317]: info: :[01mChecking for dependency: DBus - Message bus system...[0m
hp-check[3317]: info: :OK, found.
hp-check[3317]: info: :
hp-check[3317]: info: :[01mChecking for dependency: gcc - GNU Project C and C++ Compiler...[0m
hp-check[3317]: info: :OK, found.
hp-check[3317]: info: :
hp-check[3317]: info: :[01mChecking for dependency: GhostScript - PostScript and PDF language interpreter and previewer...[0m
hp-check[3317]: info: :OK, found.
hp-check[3317]: info: :
hp-check[3317]: info: :[01mChecking for dependency: libcrypto - OpenSSL cryptographic library...[0m
hp-check[3317]: info: :OK, found.
hp-check[3317]: info: :
hp-check[3317]: info: :[01mChecking for dependency: libjpeg - JPEG library...[0m
hp-check[3317]: info: :OK, found.
hp-check[3317]: info: :
hp-check[3317]: info: :[01mChecking for dependency: libnetsnmp-devel - SNMP networking library development files...[0m
hp-check[3317]: info: :OK, found.
hp-check[3317]: info: :
hp-check[3317]: info: :[01mChecking for dependency: libpthread - POSIX threads library...[0m
hp-check[3317]: info: :OK, found.
hp-check[3317]: info: :
hp-check[3317]: info: :[01mChecking for dependency: libtool - Library building support services...[0m
hp-check[3317]: info: :OK, found.
hp-check[3317]: info: :
hp-check[3317]: info: :[01mChecking for dependency: libusb - USB library...[0m
hp-check[3317]: info: :OK, found.
hp-check[3317]: info: :
hp-check[3317]: info: :[01mChecking for dependency: make - GNU make utility to maintain groups of programs...[0m
hp-check[3317]: info: :OK, found.
hp-check[3317]: info: :
hp-check[3317]: info: :[01mChecking for dependency: PIL - Python Imaging Library (required for commandline scanning with hp-scan)...[0m
hp-check[3317]: info: :OK, found.
hp-check[3317]: info: :
hp-check[3317]: info: :[01mChecking for dependency: PolicyKit - Administrative policy framework...[0m
hp-check[3317]: info: :OK, found.
hp-check[3317]: info: :
hp-check[3317]: info: :[01mChecking for dependency: PyQt 4 DBus - DBus Support for PyQt4...[0m
hp-check[3317]: info: :OK, found.
hp-check[3317]: info: :
hp-check[3317]: info: :[01mChecking for dependency: Python DBus - Python bindings for DBus...[0m
hp-check[3317]: info: :OK, found.
hp-check[3317]: info: :
hp-check[3317]: info: :[01mChecking for dependency: Python devel - Python development files...[0m
hp-check[3317]: info: :OK, found.
hp-check[3317]: info: :
hp-check[3317]: info: :[01mChecking for dependency: Python libnotify - Python bindings for the libnotify Desktop notifications...[0m
hp-check[3317]: info: :OK, found.
hp-check[3317]: info: :
hp-check[3317]: info: :[01mChecking for dependency: Python XML libraries...[0m
hp-check[3317]: info: :OK, found.
hp-check[3317]: info: :
hp-check[3317]: info: :[01mChecking for dependency: Python 2.3 or greater - Required for fax functionality...[0m
hp-check[3317]: info: :OK, found.
hp-check[3317]: info: :
hp-check[3317]: info: :[01mChecking for dependency: Python 2.2 or greater - Python programming language...[0m
hp-check[3317]: info: :OK, found.
hp-check[3317]: info: :
hp-check[3317]: info: :[01mChecking for dependency: Reportlab - PDF library for Python...[0m
hp-check[3317]: info: :OK, found.
hp-check[3317]: info: :
hp-check[3317]: info: :[01mChecking for dependency: SANE - Scanning library...[0m
hp-check[3317]: info: :OK, found.
hp-check[3317]: info: :
hp-check[3317]: info: :[01mChecking for dependency: SANE - Scanning library development files...[0m
hp-check[3317]: info: :OK, found.
hp-check[3317]: info: :
hp-check[3317]: info: :[01mChecking for dependency: scanimage - Shell scanning program...[0m
hp-check[3317]: info: :OK, found.
hp-check[3317]: info: :
hp-check[3317]: info: :[01mChecking for dependency: xsane - Graphical scanner frontend for SANE...[0m
hp-check[3317]: info: :OK, found.
hp-check[3317]: info: :
hp-check[3317]: info: :
hp-check[3317]: info: :----------------------
hp-check[3317]: info:  HPLIP INSTALLATION |
hp-check[3317]: info: :----------------------
hp-check[3317]: info: :
hp-check[3317]: info: :
hp-check[3317]: info: :[01mCurrently installed HPLIP version...[0m
hp-check[3317]: info: :HPLIP 3.10.2 currently installed in '/usr/share/hplip'.
hp-check[3317]: info: :
hp-check[3317]: info: :[01mCurrent contents of '/etc/hp/hplip.conf' file:[0m
hp-check[3317]: info: :# hplip.conf.  Generated from hplip.conf.in by configure.

[hplip]
version=3.10.2

[dirs]
home=/usr/share/hplip
run=/var/run
ppd=/usr/share/ppd/HP
ppdbase=/usr/share/ppd
doc=/usr/share/doc/hplip-3.10.2
icon=/usr/share/applications
cupsbackend=/usr/lib/cups/backend
cupsfilter=/usr/lib/cups/filter
drv=/usr/share/cups/drv/hp

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
hpijs-install=no
foomatic-drv-install=no
foomatic-ppd-install=no
foomatic-rip-hplip-install=no
hpcups-install=yes
cups-drv-install=yes
cups-ppd-install=no
internal-tag=3.10.2rc1.9
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

hp-check[3317]: info: :
hp-check[3317]: info: :[01mCurrent contents of '/var/lib/hp/hplip.state' file:[0m
hp-check[3317]: info: :[plugin]
eula = 1
installed = 1


hp-check[3317]: info: :
hp-check[3317]: info: :[01mCurrent contents of '~/.hplip/hplip.conf' file:[0m
hp-check[3317]: info: :[last_used]
printer_name = HP_LaserJet_1020
working_dir = .
device_uri = "hp:/usb/HP_LaserJet_1020?serial=JL2DP9V"

[commands]
scan = /usr/bin/simple-scan %SANE_URI%

[installation]
version = 3.10.2rc1.9
date_time = 05/02/2010 08:25:37

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


hp-check[3317]: info: :
hp-check[3317]: info: :--------------------------
hp-check[3317]: info: DISCOVERED USB DEVICES |
hp-check[3317]: info: :--------------------------
hp-check[3317]: info: :
hp-check[3317]: info: :  Device URI                        Model           
hp-check[3317]: info: :  --------------------------------  ----------------
hp-check[3317]: info: :  hp:/usb/HP_LaserJet_1020?serial=  HP LaserJet 1020
  JL2DP9V                                           
hp-check[3317]: info: :
hp-check[3317]: info: :---------------------------------
hp-check[3317]: info: INSTALLED CUPS PRINTER QUEUES |
hp-check[3317]: info: :---------------------------------
hp-check[3317]: info: :
hp-check[3317]: info: :
hp-check[3317]: info: :[01mHP_LaserJet_1020[0m
hp-check[3317]: info: :[01m----------------[0m
hp-check[3317]: info: :Type: Printer
hp-check[3317]: info: evice URI: hp:/usb/HP_LaserJet_1020?serial=JL2DP9V
hp-check[3317]: info: PD: /etc/cups/ppd/HP_LaserJet_1020.ppd
hp-check[3317]: info: PD Description: HP LaserJet 1020, hpcups 3.10.2, requires proprietary plugin
hp-check[3317]: info: rinter status: printer HP_LaserJet_1020 now printing HP_LaserJet_1020-0.  enabled since Sun 02 May 2010 08:42:43 AM HST
    Processing page 2...
hp-check[3317]: info: :Required plug-in status: Installed
error: Device busy: hp:/usb/HP_LaserJet_1020?serial=JL2DP9V
error: Device not found
error: Communication status: Failed
hp-check[3317]: info: :
hp-check[3317]: info: :
hp-check[3317]: info: :----------------------
hp-check[3317]: info:  SANE CONFIGURATION |
hp-check[3317]: info: :----------------------
hp-check[3317]: info: :
hp-check[3317]: info: :[01m'hpaio' in '/etc/sane.d/dll.conf'...[0m
hp-check[3317]: info: :OK, found. SANE backend 'hpaio' is properly set up.
hp-check[3317]: info: :
hp-check[3317]: info: :[01mChecking output of 'scanimage -L'...[0m
hp-check[3317]: info: :
No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).

hp-check[3317]: info: :
hp-check[3317]: info: :---------------------
hp-check[3317]: info:  PYTHON EXTENSIONS |
hp-check[3317]: info: :---------------------
hp-check[3317]: info: :
hp-check[3317]: info: :[01mChecking 'cupsext' CUPS extension...[0m
hp-check[3317]: info: :OK, found.
hp-check[3317]: info: :
hp-check[3317]: info: :[01mChecking 'pcardext' Photocard extension...[0m
hp-check[3317]: info: :OK, found.
hp-check[3317]: info: :
hp-check[3317]: info: :[01mChecking 'hpmudext' I/O extension...[0m
hp-check[3317]: info: :OK, found.
hp-check[3317]: info: :
hp-check[3317]: info: :[01mChecking 'scanext' SANE scanning extension...[0m
hp-check[3317]: info: :OK, found.
hp-check[3317]: info: :
hp-check[3317]: info: :
hp-check[3317]: info: :
hp-check[3317]: info: :-----------------
hp-check[3317]: info: USB I/O SETUP |
hp-check[3317]: info: :-----------------
hp-check[3317]: info: :
hp-check[3317]: info: :[01mChecking for permissions of USB attached printers...[0m
hp-check[3317]: info: :
HP Device 0x2b17 at 002:007: 
hp-check[3317]: info: :    Device URI: hp:/usb/HP_LaserJet_1020?serial=JL2DP9V
hp-check[3317]: info: :    Device node: /dev/bus/usb/002/007
hp-check[3317]: info: :    Mode: 0664
hp-check[3317]: info: :getfacl: Removing leading '/' from absolute path names
# file: dev/bus/usb/002/007
# owner: root
# group: lp
user::rw-
user:richard:rw-
group::rw-
mask::rw-
other::r--


hp-check[3317]: info: :
hp-check[3317]: info: :---------------
hp-check[3317]: info:  USER GROUPS |
hp-check[3317]: info: :---------------
hp-check[3317]: info: :
hp-check[3317]: info: :root lp lpadmin

hp-check[3317]: info: :
hp-check[3317]: info: :-----------
hp-check[3317]: info: SUMMARY |
hp-check[3317]: info: :-----------
hp-check[3317]: info: :
error: 1 error or warning.
hp-check[3317]: info: :
hp-check[3317]: info: lease refer to the installation instructions at:
hp-check[3317]: info: :[http://hplip.sourceforge.net/install/index.html](http://hplip.sourceforge.net/install/index.html)

hp-check[3317]: info: :
hp-check[3317]: info: Done.

---

### Post by Jason Argonaut on 2010-05-13
Same problem, but with Canon MX320 all-in-1.

---

### Post by Paeone on 2010-05-13
Canon MP 750 network printer not working with Ubuntu 10.4.
Printer is being detected, here's the bug report, can anyone help:

Page 1 (Scheduler not running?):
{'cups_connection_failure': False}
Page 2 (Choose printer):
{'cups_dest': <cups.Dest Canon_MP750 (default)>,
 'cups_instance': None,
 'cups_queue': 'Canon_MP750',
 'cups_queue_listed': True}
Page 3 (Check printer sanity):
{'cups_device_uri_scheme': u'file',
 'cups_printer_dict': {'device-uri': u'file:///dev/null',
                       'printer-info': u'Canon_MP750',
                       'printer-is-shared': True,
                       'printer-location': u'',
                       'printer-make-and-model': u'Local Raw Printer',
                       'printer-state': 3,
                       'printer-state-message': u'',
                       'printer-state-reasons': [u'none'],
                       'printer-type': 131076,
                       'printer-uri-supported': u'ipp://localhost:631/printers/Canon_MP750'},
 'cups_printer_remote': False,
 'is_cups_class': False,
 'local_cups_queue_attributes': {'auth-info-required': u'none',
                                 'charset-configured': u'utf-8',
                                 'charset-supported': [u'us-ascii', u'utf-8'],
                                 'compression-supported': [u'none', u'gzip'],
                                 'copies-default': 1,
                                 'copies-supported': (1, 9999),
                                 'cups-version': u'1.4.3',
                                 'device-uri': u'file:///dev/null',
                                 'document-format-default': u'application/octet-stream',
                                 'document-format-supported': [u'application/octet-stream',
                                                               u'application/openofficeps',
                                                               u'application/pdf',
                                                               u'application/postscript',
                                                               u'application/rss+xml',
                                                               u'application/vnd.cups-banner',
                                                               u'application/vnd.cups-command',
                                                               u'application/vnd.cups-pdf',
                                                               u'application/vnd.cups-postscript',
                                                               u'application/vnd.cups-ppd',
                                                               u'application/vnd.cups-raster',
                                                               u'application/vnd.cups-raw',
                                                               u'application/vnd.hp-hpgl',
                                                               u'application/x-cshell',
                                                               u'application/x-csource',
                                                               u'application/x-perl',
                                                               u'application/x-shell',
                                                               u'image/gif',
                                                               u'image/jpeg',
                                                               u'image/png',
                                                               u'image/tiff',
                                                               u'image/x-alias',
                                                               u'image/x-bitmap',
                                                               u'image/x-icon',
                                                               u'image/x-photocd',
                                                               u'image/x-portable-anymap',
                                                               u'image/x-portable-bitmap',
                                                               u'image/x-portable-graymap',
                                                               u'image/x-portable-pixmap',
                                                               u'image/x-sgi-rgb',
                                                               u'image/x-sun-raster',
                                                               u'image/x-xbitmap',
                                                               u'image/x-xpixmap',
                                                               u'image/x-xwindowdump',
                                                               u'text/css',
                                                               u'text/html',
                                                               u'text/plain'],
                                 'finishings-default': 3,
                                 'finishings-supported': [3],
                                 'generated-natural-language-supported': [u'en_US'],
                                 'ipp-versions-supported': [u'1.0',
                                                            u'1.1',
                                                            u'2.0',
                                                            u'2.1'],
                                 'job-hold-until-default': u'no-hold',
                                 'job-hold-until-supported': [u'no-hold',
                                                              u'indefinite',
                                                              u'day-time',
                                                              u'evening',
                                                              u'night',
                                                              u'second-shift',
                                                              u'third-shift',
                                                              u'weekend'],
                                 'job-k-limit': 0,
                                 'job-page-limit': 0,
                                 'job-priority-default': 50,
                                 'job-priority-supported': [100],
                                 'job-quota-period': 0,
                                 'job-settable-attributes-supported': [u'copies',
                                                                       u'finishings',
                                                                       u'job-hold-until',
                                                                       u'job-priority',
                                                                       u'media',
                                                                       u'multiple-document-handling',
                                                                       u'number-up',
                                                                       u'orientation-requested',
                                                                       u'page-ranges',
                                                                       u'print-quality',
                                                                       u'printer-resolution',
                                                                       u'sides'],
                                 'job-sheets-default': (u'none', u'none'),
                                 'job-sheets-supported': [u'none',
                                                          u'classified',
                                                          u'confidential',
                                                          u'secret',
                                                          u'standard',
                                                          u'topsecret',
                                                          u'unclassified'],
                                 'marker-change-time': 0,
                                 'media-col-supported': [u'media-color',
                                                         u'media-key',
                                                         u'media-size',
                                                         u'media-type'],
                                 'multiple-document-handling-supported': [u'separate-documents-uncollated-copies',
                                                                          u'separate-documents-collated-copies'],
                                 'multiple-document-jobs-supported': True,
                                 'multiple-operation-time-out': 300,
                                 'natural-language-configured': u'en_US',
                                 'notify-attributes-supported': [u'printer-state-change-time',
                                                                 u'notify-lease-expiration-time',
                                                                 u'notify-subscriber-user-name'],
                                 'notify-events-default': [u'job-completed'],
                                 'notify-events-supported': [u'job-completed',
                                                             u'job-config-changed',
                                                             u'job-created',
                                                             u'job-progress',
                                                             u'job-state-changed',
                                                             u'job-stopped',
                                                             u'printer-added',
                                                             u'printer-changed',
                                                             u'printer-config-changed',
                                                             u'printer-deleted',
                                                             u'printer-finishings-changed',
                                                             u'printer-media-changed',
                                                             u'printer-modified',
                                                             u'printer-restarted',
                                                             u'printer-shutdown',
                                                             u'printer-state-changed',
                                                             u'printer-stopped',
                                                             u'server-audit',
                                                             u'server-restarted',
                                                             u'server-started',
                                                             u'server-stopped'],
                                 'notify-lease-duration-default': 86400,
                                 'notify-lease-duration-supported': (0,
                                                                     2147483647),
                                 'notify-max-events-supported': [100],
                                 'notify-pull-method-supported': [u'ippget'],
                                 'notify-schemes-supported': [u'dbus',
                                                              u'mailto',
                                                              u'rss'],
                                 'number-up-default': 1,
                                 'number-up-supported': [1, 2, 4, 6, 9, 16],
                                 'operations-supported': [2,
                                                          4,
                                                          5,
                                                          6,
                                                          8,
                                                          9,
                                                          10,
                                                          11,
                                                          12,
                                                          13,
                                                          16,
                                                          17,
                                                          18,
                                                          19,
                                                          20,
                                                          21,
                                                          22,
                                                          23,
                                                          24,
                                                          25,
                                                          26,
                                                          27,
                                                          28,
                                                          34,
                                                          35,
                                                          37,
                                                          38,
                                                          16385,
                                                          16386,
                                                          16387,
                                                          16388,
                                                          16389,
                                                          16390,
                                                          16391,
                                                          16392,
                                                          16393,
                                                          16394,
                                                          16395,
                                                          16396,
                                                          16397,
                                                          16398,
                                                          16399,
                                                          16423],
                                 'orientation-requested-default': None,
                                 'orientation-requested-supported': [3,
                                                                     4,
                                                                     5,
                                                                     6],
                                 'page-ranges-supported': True,
                                 'pdl-override-supported': [u'not-attempted'],
                                 'printer-current-time': '(IPP_TAG_DATE)',
                                 'printer-error-policy': u'retry-job',
                                 'printer-error-policy-supported': [u'abort-job',
                                                                    u'retry-current-job',
                                                                    u'retry-job',
                                                                    u'stop-printer'],
                                 'printer-info': u'Canon_MP750',
                                 'printer-is-accepting-jobs': True,
                                 'printer-is-shared': True,
                                 'printer-location': u'',
                                 'printer-make-and-model': u'Local Raw Printer',
                                 'printer-more-info': u'http://localhost:631/printers/Canon_MP750',
                                 'printer-name': u'Canon_MP750',
                                 'printer-op-policy': u'default',
                                 'printer-op-policy-supported': [u'authenticated',
                                                                 u'default'],
                                 'printer-settable-attributes-supported': [u'printer-info',
                                                                           u'printer-location'],
                                 'printer-state': 3,
                                 'printer-state-change-time': 1273747418,
                                 'printer-state-message': u'',
                                 'printer-state-reasons': [u'none'],
                                 'printer-type': 131076,
                                 'printer-up-time': 1273747480,
                                 'printer-uri-supported': [u'ipp://localhost:631/printers/Canon_MP750'],
                                 'queued-job-count': 0,
                                 'server-is-sharing-printers': True,
                                 'uri-authentication-supported': [u'requesting-user-name'],
                                 'uri-security-supported': [u'none']}}
Page 4 (Local or remote?):
{'printer_is_remote': False}
Page 5 (Error log checkpoint):
{'cups_server_settings': {'BrowseLocalProtocols': 'CUPS dnssd',
                          'BrowseRemoteProtocols': 'CUPS',
                          'DefaultAuthType': 'Basic',
                          'MaxLogSize': '0',
                          'SystemGroup': 'lpadmin',
                          '_debug_logging': '1',
                          '_remote_admin': '1',
                          '_remote_any': '1',
                          '_remote_printers': '1',
                          '_share_printers': '1',
                          '_user_cancel_any': '0'},
 'error_log_checkpoint': 77492086L}
Page 6 (Print test page):
{'test_page_attempted': '13/Mai/2010:12:45:01 +0000',
 'test_page_completions': [(42, u'Job completed.')],
 'test_page_job_id': [42],
 'test_page_job_status': [(True,
                           42,
                           'Canon_MP750',
                           'Test Page',
                           'Abgeschlossen',
                           {'attributes-charset': u'utf-8',
                            'attributes-natural-language': u'de-de',
                            'document-count': 0,
                            'document-format': u'application/vnd.cups-banner',
                            'job-hold-until': u'no-hold',
                            'job-id': 42,
                            'job-k-octets': 1,
                            'job-media-progress': 0,
                            'job-media-sheets-completed': 1,
                            'job-more-info': u'ipp://localhost:631/jobs/42',
                            'job-name': u'Test Page',
                            'job-originating-host-name': u'localhost',
                            'job-originating-user-name': u'cleve',
                            'job-preserved': False,
                            'job-printer-state-message': u'',
                            'job-printer-state-reasons': [u'none'],
                            'job-printer-up-time': 1273747527,
                            'job-printer-uri': u'ipp://lidocrew-laptop:631/printers/Canon_MP750',
                            'job-priority': 50,
                            'job-sheets': [u'none', u'none'],
                            'job-state': 9,
                            'job-state-reasons': u'job-completed-successfully',
                            'job-uri': u'ipp://localhost:631/jobs/42',
                            'job-uuid': u'urn:uuid:de65cc88-3823-337a-7db0-eb782e156e32',
                            'printer-uri': u'ipp://localhost/printers/Canon_MP750',
                            'time-at-completed': 1273747501,
                            'time-at-creation': 1273747501,
                            'time-at-processing': 1273747501})],
 'test_page_successful': False}
Page 7 (Error log fetch):
{'error_log': ['D [13/May/2010:12:44:56 +0200] cupsdSetBusyState: Not busy',
               'D [13/May/2010:12:44:57 +0200] cupsdReadClient: 27 POST / HTTP/1.1',
               'D [13/May/2010:12:44:57 +0200] cupsdSetBusyState: Active clients',
               'D [13/May/2010:12:44:57 +0200] cupsdAuthorize: Authorized as cleve using PeerCred',
               'D [13/May/2010:12:44:57 +0200] cupsdReadClient: 27 1.1 Get-Jobs 1',
               'D [13/May/2010:12:44:57 +0200] Get-Jobs ipp://localhost/printers/',
               'D [13/May/2010:12:44:57 +0200] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost',
               'D [13/May/2010:12:44:57 +0200] cupsdSetBusyState: Not busy',
               'D [13/May/2010:12:44:57 +0200] cupsdReadClient: 27 POST / HTTP/1.1',
               'D [13/May/2010:12:44:57 +0200] cupsdSetBusyState: Active clients',
               'D [13/May/2010:12:44:57 +0200] cupsdAuthorize: Authorized as cleve using PeerCred',
               'D [13/May/2010:12:44:57 +0200] cupsdReadClient: 27 1.1 Get-Jobs 1',
               'D [13/May/2010:12:44:57 +0200] Get-Jobs ipp://localhost/printers/',
               'D [13/May/2010:12:44:57 +0200] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost',
               'D [13/May/2010:12:44:57 +0200] cupsdSetBusyState: Not busy',
               'D [13/May/2010:12:44:57 +0200] cupsdReadClient: 27 POST / HTTP/1.1',
               'D [13/May/2010:12:44:57 +0200] cupsdSetBusyState: Active clients',
               'D [13/May/2010:12:44:57 +0200] cupsdAuthorize: Authorized as cleve using PeerCred',
               'D [13/May/2010:12:44:57 +0200] cupsdReadClient: 27 1.1 Create-Printer-Subscription 1',
               'D [13/May/2010:12:44:57 +0200] Create-Printer-Subscription /',
               'D [13/May/2010:12:44:57 +0200] cupsdCreateSubscription(con=0x20b099c8(27), uri="/")',
               'D [13/May/2010:12:44:57 +0200] pullmethod="ippget"',
               'D [13/May/2010:12:44:57 +0200] notify-lease-duration=86400',
               'D [13/May/2010:12:44:57 +0200] notify-time-interval=0',
               'D [13/May/2010:12:44:57 +0200] cupsdAddSubscription(mask=17800, dest=(nil)(), job=(nil)(0), uri="(null)")',
               'D [13/May/2010:12:44:57 +0200] Added subscription 62 for server',
               'D [13/May/2010:12:44:57 +0200] cupsdMarkDirty(-----S)',
               'D [13/May/2010:12:44:57 +0200] cupsdSetBusyState: Active clients and dirty files',
               'D [13/May/2010:12:44:57 +0200] Returning IPP successful-ok for Create-Printer-Subscription (/) from localhost',
               'D [13/May/2010:12:44:57 +0200] cupsdSetBusyState: Dirty files',
               'D [13/May/2010:12:44:58 +0200] cupsdReadClient: 27 POST / HTTP/1.1',
               'D [13/May/2010:12:44:58 +0200] cupsdSetBusyState: Active clients and dirty files',
               'D [13/May/2010:12:44:58 +0200] cupsdAuthorize: Authorized as cleve using PeerCred',
               'D [13/May/2010:12:44:58 +0200] cupsdReadClient: 27 1.1 Get-Notifications 1',
               'D [13/May/2010:12:44:58 +0200] Get-Notifications /',
               'D [13/May/2010:12:44:58 +0200] cupsdIsAuthorized: username="cleve"',
               'D [13/May/2010:12:44:58 +0200] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [13/May/2010:12:44:58 +0200] cupsdSetBusyState: Dirty files',
               'D [13/May/2010:12:45:01 +0200] cupsdAcceptClient: 28 from localhost (Domain)',
               'D [13/May/2010:12:45:01 +0200] cupsdReadClient: 28 POST /printers/Canon_MP750 HTTP/1.1',
               'D [13/May/2010:12:45:01 +0200] cupsdSetBusyState: Active clients and dirty files',
               'D [13/May/2010:12:45:01 +0200] cupsdAuthorize: No authentication data provided.',
               'D [13/May/2010:12:45:01 +0200] cupsdReadClient: 28 1.1 Print-Job 1',
               'D [13/May/2010:12:45:01 +0200] Print-Job ipp://localhost/printers/Canon_MP750',
               'D [13/May/2010:12:45:01 +0200] [Job ???] Auto-typing file...',
               'I [13/May/2010:12:45:01 +0200] [Job ???] Request file type is application/vnd.cups-banner.',
               'D [13/May/2010:12:45:01 +0200] cupsdMarkDirty(----J-)',
               'D [13/May/2010:12:45:01 +0200] add_job: requesting-user-name="cleve"',
               'D [13/May/2010:12:45:01 +0200] Adding default job-sheets values "none,none"...',
               'I [13/May/2010:12:45:01 +0200] [Job 42] Adding start banner page "none".',
               'D [13/May/2010:12:45:01 +0200] cupsdMarkDirty(-----S)',
               'D [13/May/2010:12:45:01 +0200] cupsdMarkDirty(----J-)',
               'I [13/May/2010:12:45:01 +0200] [Job 42] Adding end banner page "none".',
               'I [13/May/2010:12:45:01 +0200] [Job 42] File of type application/vnd.cups-banner queued by "cleve".',
               'D [13/May/2010:12:45:01 +0200] [Job 42] hold_until=0',
               'I [13/May/2010:12:45:01 +0200] [Job 42] Queued on "Canon_MP750" by "cleve".',
               'D [13/May/2010:12:45:01 +0200] cupsdMarkDirty(----J-)',
               'D [13/May/2010:12:45:01 +0200] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [13/May/2010:12:45:01 +0200] cupsdMarkDirty(-----S)',
               'D [13/May/2010:12:45:01 +0200] [Job 42] Sending job to queue tagged as raw...',
               'D [13/May/2010:12:45:01 +0200] [Job 42] job-sheets=none,none',
               'D [13/May/2010:12:45:01 +0200] [Job 42] argv[0]="Canon_MP750"',
               'D [13/May/2010:12:45:01 +0200] [Job 42] argv[1]="42"',
               'D [13/May/2010:12:45:01 +0200] [Job 42] argv[2]="cleve"',
               'D [13/May/2010:12:45:01 +0200] [Job 42] argv[3]="Test Page"',
               'D [13/May/2010:12:45:01 +0200] [Job 42] argv[4]="1"',
               'D [13/May/2010:12:45:01 +0200] [Job 42] argv[5]="job-uuid=urn:uuid:de65cc88-3823-337a-7db0-eb782e156e32 job-originating-host-name=localhost"',
               'D [13/May/2010:12:45:01 +0200] [Job 42] argv[6]="/var/spool/cups/d00042-001"',
               'D [13/May/2010:12:45:01 +0200] [Job 42] envp[0]="CUPS_CACHEDIR=/var/cache/cups"',
               'D [13/May/2010:12:45:01 +0200] [Job 42] envp[1]="CUPS_DATADIR=/usr/share/cups"',
               'D [13/May/2010:12:45:01 +0200] [Job 42] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"',
               'D [13/May/2010:12:45:01 +0200] [Job 42] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"',
               'D [13/May/2010:12:45:01 +0200] [Job 42] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"',
               'D [13/May/2010:12:45:01 +0200] [Job 42] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"',
               'D [13/May/2010:12:45:01 +0200] [Job 42] envp[6]="CUPS_SERVERROOT=/etc/cups"',
               'D [13/May/2010:12:45:01 +0200] [Job 42] envp[7]="CUPS_STATEDIR=/var/run/cups"',
               'D [13/May/2010:12:45:01 +0200] [Job 42] envp[8]="HOME=/var/spool/cups/tmp"',
               'D [13/May/2010:12:45:01 +0200] [Job 42] envp[9]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"',
               'D [13/May/2010:12:45:01 +0200] [Job 42] envp[10]="SERVER_ADMIN=root@lidocrew-laptop"',
               'D [13/May/2010:12:45:01 +0200] [Job 42] envp[11]="SOFTWARE=CUPS/1.4.3"',
               'D [13/May/2010:12:45:01 +0200] [Job 42] envp[12]="TMPDIR=/var/spool/cups/tmp"',
               'D [13/May/2010:12:45:01 +0200] [Job 42] envp[13]="TZ=Europe/Berlin"',
               'D [13/May/2010:12:45:01 +0200] [Job 42] envp[14]="USER=root"',
               'D [13/May/2010:12:45:01 +0200] [Job 42] envp[15]="CUPS_SERVER=/var/run/cups/cups.sock"',
               'D [13/May/2010:12:45:01 +0200] [Job 42] envp[16]="CUPS_ENCRYPTION=IfRequested"',
               'D [13/May/2010:12:45:01 +0200] [Job 42] envp[17]="IPP_PORT=631"',
               'D [13/May/2010:12:45:01 +0200] [Job 42] envp[18]="CHARSET=utf-8"',
               'D [13/May/2010:12:45:01 +0200] [Job 42] envp[19]="LANG=de_DE.UTF-8"',
               'D [13/May/2010:12:45:01 +0200] [Job 42] envp[20]="PPD=/etc/cups/ppd/Canon_MP750.ppd"',
               'D [13/May/2010:12:45:01 +0200] [Job 42] envp[21]="RIP_MAX_CACHE=512991k"',
               'D [13/May/2010:12:45:01 +0200] [Job 42] envp[22]="CONTENT_TYPE=application/vnd.cups-banner"',
               'D [13/May/2010:12:45:01 +0200] [Job 42] envp[23]="DEVICE_URI=file:///dev/null"',
               'D [13/May/2010:12:45:01 +0200] [Job 42] envp[24]="PRINTER_INFO=Canon_MP750"',
               'D [13/May/2010:12:45:01 +0200] [Job 42] envp[25]="PRINTER_LOCATION="',
               'D [13/May/2010:12:45:01 +0200] [Job 42] envp[26]="PRINTER=Canon_MP750"',
               'D [13/May/2010:12:45:01 +0200] [Job 42] envp[27]="CUPS_FILETYPE=document"',
               'I [13/May/2010:12:45:01 +0200] [Job 42] Started filter /usr/lib/cups/filter/gziptoany (PID 4424)',
               'D [13/May/2010:12:45:01 +0200] cupsdMarkDirty(-----S)',
               'D [13/May/2010:12:45:01 +0200] Returning IPP successful-ok for Print-Job (ipp://localhost/printers/Canon_MP750) from localhost',
               'D [13/May/2010:12:45:01 +0200] cupsdSetBusyState: Printing jobs and dirty files',
               'D [13/May/2010:12:45:01 +0200] [Job 42] PAGE: 1 1',
               'D [13/May/2010:12:45:01 +0200] cupsdMarkDirty(-----S)',
               'D [13/May/2010:12:45:01 +0200] PID 4424 (/usr/lib/cups/filter/gziptoany) exited with no errors.',
               'D [13/May/2010:12:45:01 +0200] cupsdMarkDirty(-----S)',
               'I [13/May/2010:12:45:01 +0200] [Job 42] Job completed.',
               'D [13/May/2010:12:45:01 +0200] cupsdMarkDirty(----J-)',
               'D [13/May/2010:12:45:01 +0200] cupsdMarkDirty(-----S)',
               'D [13/May/2010:12:45:01 +0200] cupsdAcceptClient: 29 from localhost (Domain)',
               'D [13/May/2010:12:45:01 +0200] cupsdReadClient: 29 POST / HTTP/1.1',
               'D [13/May/2010:12:45:01 +0200] cupsdSetBusyState: Active clients and dirty files',
               'D [13/May/2010:12:45:01 +0200] cupsdAuthorize: No authentication data provided.',
               'D [13/May/2010:12:45:01 +0200] cupsdReadClient: 29 1.1 Get-Notifications 1',
               'D [13/May/2010:12:45:01 +0200] Get-Notifications /',
               'D [13/May/2010:12:45:01 +0200] cupsdIsAuthorized: requesting-user-name="cleve"',
               'D [13/May/2010:12:45:01 +0200] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [13/May/2010:12:45:01 +0200] cupsdAcceptClient: 30 from localhost (Domain)',
               'D [13/May/2010:12:45:01 +0200] cupsdReadClient: 30 POST / HTTP/1.1',
               'D [13/May/2010:12:45:01 +0200] cupsdAuthorize: No authentication data provided.',
               'D [13/May/2010:12:45:01 +0200] cupsdReadClient: 30 1.1 Get-Notifications 1',
               'D [13/May/2010:12:45:01 +0200] Get-Notifications /',
               'D [13/May/2010:12:45:01 +0200] cupsdIsAuthorized: requesting-user-name="cleve"',
               'D [13/May/2010:12:45:01 +0200] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [13/May/2010:12:45:01 +0200] cupsdSetBusyState: Dirty files',
               'D [13/May/2010:12:45:01 +0200] cupsdReadClient: 29 POST / HTTP/1.1',
               'D [13/May/2010:12:45:01 +0200] cupsdSetBusyState: Active clients and dirty files',
               'D [13/May/2010:12:45:01 +0200] cupsdAuthorize: No authentication data provided.',
               'D [13/May/2010:12:45:01 +0200] cupsdReadClient: 29 1.1 Get-Job-Attributes 1',
               'D [13/May/2010:12:45:01 +0200] Get-Job-Attributes ipp://localhost/jobs/42',
               'D [13/May/2010:12:45:01 +0200] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/42) from localhost',
               'D [13/May/2010:12:45:01 +0200] cupsdReadClient: 30 WAITING Closing on EOF',
               'D [13/May/2010:12:45:01 +0200] cupsdCloseClient: 30',
               'D [13/May/2010:12:45:01 +0200] cupsdSetBusyState: Dirty files',
               'D [13/May/2010:12:45:01 +0200] cupsdReadClient: 14 POST / HTTP/1.1',
               'D [13/May/2010:12:45:01 +0200] cupsdSetBusyState: Active clients and dirty files',
               'D [13/May/2010:12:45:01 +0200] cupsdAuthorize: No authentication data provided.',
               'D [13/May/2010:12:45:01 +0200] cupsdReadClient: 27 POST / HTTP/1.1',
               'D [13/May/2010:12:45:01 +0200] cupsdAuthorize: Authorized as cleve using PeerCred',
               'D [13/May/2010:12:45:01 +0200] cupsdReadClient: 27 1.1 Get-Notifications 1',
               'D [13/May/2010:12:45:01 +0200] Get-Notifications /',
               'D [13/May/2010:12:45:01 +0200] cupsdIsAuthorized: username="cleve"',
               'D [13/May/2010:12:45:01 +0200] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [13/May/2010:12:45:01 +0200] cupsdReadClient: 14 1.1 CUPS-Get-Printers 1',
               'D [13/May/2010:12:45:01 +0200] CUPS-Get-Printers',
               'D [13/May/2010:12:45:01 +0200] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost',
               'D [13/May/2010:12:45:01 +0200] cupsdReadClient: 14 POST / HTTP/1.1',
               'D [13/May/2010:12:45:01 +0200] cupsdAuthorize: No authentication data provided.',
               'D [13/May/2010:12:45:01 +0200] cupsdReadClient: 14 1.1 CUPS-Get-Classes 1',
               'D [13/May/2010:12:45:01 +0200] CUPS-Get-Classes',
               'D [13/May/2010:12:45:01 +0200] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost',
               'D [13/May/2010:12:45:01 +0200] cupsdReadClient: 14 POST / HTTP/1.1',
               'D [13/May/2010:12:45:01 +0200] cupsdAuthorize: No authentication data provided.',
               'D [13/May/2010:12:45:01 +0200] cupsdReadClient: 14 1.1 CUPS-Get-Default 1',
               'D [13/May/2010:12:45:01 +0200] CUPS-Get-Default',
               'D [13/May/2010:12:45:01 +0200] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost',
               'D [13/May/2010:12:45:01 +0200] cupsdSetBusyState: Dirty files',
               'D [13/May/2010:12:45:01 +0200] cupsdReadClient: 14 POST / HTTP/1.1',
               'D [13/May/2010:12:45:01 +0200] cupsdSetBusyState: Active clients and dirty files',
               'D [13/May/2010:12:45:01 +0200] cupsdAuthorize: No authentication data provided.',
               'D [13/May/2010:12:45:01 +0200] cupsdReadClient: 14 1.1 CUPS-Get-Printers 1',
               'D [13/May/2010:12:45:01 +0200] CUPS-Get-Printers',
               'D [13/May/2010:12:45:01 +0200] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost',
               'D [13/May/2010:12:45:01 +0200] cupsdSetBusyState: Dirty files',
               'D [13/May/2010:12:45:01 +0200] cupsdReadClient: 14 POST / HTTP/1.1',
               'D [13/May/2010:12:45:01 +0200] cupsdSetBusyState: Active clients and dirty files',
               'D [13/May/2010:12:45:01 +0200] cupsdAuthorize: No authentication data provided.',
               'D [13/May/2010:12:45:01 +0200] cupsdReadClient: 14 1.1 CUPS-Get-Classes 1',
               'D [13/May/2010:12:45:01 +0200] CUPS-Get-Classes',
               'D [13/May/2010:12:45:01 +0200] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost',
               'D [13/May/2010:12:45:01 +0200] cupsdSetBusyState: Dirty files',
               'D [13/May/2010:12:45:01 +0200] cupsdReadClient: 14 POST / HTTP/1.1',
               'D [13/May/2010:12:45:01 +0200] cupsdSetBusyState: Active clients and dirty files',
               'D [13/May/2010:12:45:01 +0200] cupsdAuthorize: No authentication data provided.',
               'D [13/May/2010:12:45:01 +0200] cupsdReadClient: 14 1.1 CUPS-Get-Default 1',
               'D [13/May/2010:12:45:01 +0200] CUPS-Get-Default',
               'D [13/May/2010:12:45:01 +0200] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost',
               'D [13/May/2010:12:45:01 +0200] cupsdSetBusyState: Dirty files',
               'D [13/May/2010:12:45:01 +0200] cupsdAcceptClient: 30 from localhost (Domain)',
               'D [13/May/2010:12:45:01 +0200] cupsdReadClient: 21 WAITING Closing on EOF',
               'D [13/May/2010:12:45:01 +0200] cupsdCloseClient: 21',
               'D [13/May/2010:12:45:01 +0200] cupsdReadClient: 30 POST / HTTP/1.1',
               'D [13/May/2010:12:45:01 +0200] cupsdSetBusyState: Active clients and dirty files',
               'D [13/May/2010:12:45:01 +0200] cupsdAuthorize: No authentication data provided.',
               'D [13/May/2010:12:45:01 +0200] cupsdReadClient: 30 1.1 Get-Printer-Attributes 1',
               'D [13/May/2010:12:45:01 +0200] Get-Printer-Attributes ipp://lidocrew-laptop:631/printers/Canon_MP750',
               'D [13/May/2010:12:45:01 +0200] Returning IPP successful-ok for Get-Printer-Attributes (ipp://lidocrew-laptop:631/printers/Canon_MP750) from localhost',
               'D [13/May/2010:12:45:01 +0200] cupsdSetBusyState: Dirty files',
               'D [13/May/2010:12:45:01 +0200] cupsdReadClient: 29 WAITING Closing on EOF',
               'D [13/May/2010:12:45:01 +0200] cupsdCloseClient: 29',
               'D [13/May/2010:12:45:27 +0200] cupsdReadClient: 27 POST / HTTP/1.1',
               'D [13/May/2010:12:45:27 +0200] cupsdSetBusyState: Active clients and dirty files',
               'D [13/May/2010:12:45:27 +0200] cupsdAuthorize: Authorized as cleve using PeerCred',
               'I [13/May/2010:12:45:27 +0200] Saving job cache file "/var/cache/cups/job.cache"...',
               'I [13/May/2010:12:45:27 +0200] Saving subscriptions.conf...',
               'D [13/May/2010:12:45:27 +0200] cupsdSetBusyState: Active clients',
               'D [13/May/2010:12:45:27 +0200] cupsdReadClient: 27 1.1 Get-Job-Attributes 1',
               'D [13/May/2010:12:45:27 +0200] Get-Job-Attributes ipp://localhost/jobs/42',
               'D [13/May/2010:12:45:27 +0200] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/42) from localhost',
               'D [13/May/2010:12:45:27 +0200] cupsdSetBusyState: Not busy',
               'D [13/May/2010:12:45:27 +0200] cupsdReadClient: 27 POST / HTTP/1.1',
               'D [13/May/2010:12:45:27 +0200] cupsdSetBusyState: Active clients',
               'D [13/May/2010:12:45:27 +0200] cupsdAuthorize: Authorized as cleve using PeerCred',
               'D [13/May/2010:12:45:27 +0200] cupsdReadClient: 27 1.1 Cancel-Subscription 1',
               'D [13/May/2010:12:45:27 +0200] Cancel-Subscription /',
               'D [13/May/2010:12:45:27 +0200] cupsdIsAuthorized: username="cleve"',
               'D [13/May/2010:12:45:27 +0200] cupsdMarkDirty(-----S)',
               'D [13/May/2010:12:45:27 +0200] cupsdSetBusyState: Active clients and dirty files',
               'D [13/May/2010:12:45:27 +0200] Returning IPP successful-ok for Cancel-Subscription (/) from localhost',
               'D [13/May/2010:12:45:27 +0200] cupsdSetBusyState: Dirty files',
               'D [13/May/2010:12:45:27 +0200] cupsdAcceptClient: 21 from localhost (Domain)',
               'D [13/May/2010:12:45:27 +0200] cupsdReadClient: 21 GET /admin/log/error_log HTTP/1.1',
               'D [13/May/2010:12:45:27 +0200] cupsdSetBusyState: Active clients and dirty files',
               'D [13/May/2010:12:45:27 +0200] cupsdAuthorize: No authentication data provided.']}
Page 8 (Locale issues):
{'printer_page_size': None,
 'system_locale_lang': None,
 'user_locale_ctype': 'de_DE',
 'user_locale_messages': 'de_DE'}

---

### Post by richard650 on 2010-05-27
just as an update: No solution to this  problem after one month of posting and searching.
 Richard

---

### Post by rkofler on 2010-06-29
have alook at:
[https://bugs.launchpad.net/ubuntu/+source/cups/+bug/436544](https://bugs.launchpad.net/ubuntu/+source/cups/+bug/436544)

which tells you:
solved! I did a
[HTML] rk@gobi:~$ sudo chmod 755 /usr/bin/foomatic-rip
 rk@gobi:~$ ll /usr/bin/foomatic-rip
 -rwxr-xr-x 1 root root 97976 2010-02-15 18:02 /usr/bin/foomatic-rip*
 rk@gobi:~$ sudo /etc/init.d/cups restart
  * Restarting Common Unix Printing System: cupsd[/HTML] and works!
btw: I use ubuntu 10.4

---

### Post by inzpektor on 2010-06-30
> **rkofler said:**
> [HTML] rk@gobi:~$ sudo chmod 755 /usr/bin/foomatic-rip
 rk@gobi:~$ sudo /etc/init.d/cups restart
[/HTML] and works!

Didn't work for me.  I'm using Ubuntu 10.04 with a HP LaserJet 1020.  It might be worth mentioning that I've experienced this problem with pretty much all Ubuntu versions since 5.04 Hoary Hedgehog.  Sometimes physically turning the printer off and back on seems to work, but right now it's stuck in non-working mode.

I once had an idea that the problem occurred when a job was printing outside the margins or was otherwise erroneous, and that that caused the printer to go offline ("The printer might not be connected"-message)

If Hewlet Packard is at all interested in customer-support, it might be time for them to help out with a driver for their printer that some of us have been waiting 5 years for.

---

### Post by Gerard08 on 2010-07-02
My HP 1018 has worked fine for over a year under ubuntu 8.10 and 9.10.  Without warning the connection has just stopped--printer not recognized. Usual fixes not worked nor reinstall of hplp. I'm without ideas despite posting on launch-pad. ger

---

### Post by richard650 on 2010-09-06
This finally solved my problem:

[http://foo2zjs.rkkda.com](http://foo2zjs.rkkda.com)

NOTE: 

usb://HP/LaserJet%201020

worked. NOT

usb:/dev/usb/lp0

(see Printer Properties > Device URI).

---

### Post by milos.forman on 2011-08-14
If you ride Lucid make sure that you have **foo2zjs** driver (*support for printing to ZjStream-based printers*)  installed. You can install the driver using Synaptic. It works with HP  LaserJet 1000/1005/1018/1020/1022; After you install the driver, plug  the printer into the usb port and turn in on. You'll get an wizard which  will help you configure the printer. You just need to download HP  support from their website. (option d). And that's all folks :smile:

---

