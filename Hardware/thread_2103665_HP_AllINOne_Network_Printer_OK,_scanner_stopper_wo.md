---
title: "HP AllINOne Network Printer OK, scanner stopper working"
date: 2013-01-10
forum: Hardware
---

### Post by mynot on 2013-01-10
I have an HP Officejet 4500 connected on a LAN to a computer running Xubuntu 12.04. It has been working OK for years. Suddenly I can still print but all scanning software, including Xsane says "No devices found". I've spent 2 hours on it so far but all the hp and sane reporting tools that I've tried fail to find it even after HPLIP and SANE have been re-installed. Can someone direct me to, or give me, a systematic fault-finding procedure please.
Thanks

---

### Post by mynot on 2013-01-15
More hours wasted. I have ascertained the scanner works to another pc on the network. The output of hp-check -rt is:

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
Linux tony-desktop 3.2.0-35-generic #55-Ubuntu SMP Wed Dec 5 17:45:18 UTC 2012 i686 i686 i386 GNU/Linux

Distribution:
ubuntu 12.04

Checking Python version...
OK, version 2.7.3 installed

Checking PyQt 4.x version...
OK, version 4.9.1 installed.

Checking for CUPS...
Status: scheduler is running
error_log is set to level: warn

Checking for dbus/python-dbus...
dbus daemon is running.
python-dbus version: 1.0.0


------------------------
| RUNTIME DEPENDENCIES |
------------------------


Checking for dependency: CUPS - Common Unix Printing System...
OK, found.

Checking for dependency: CUPS DDK - CUPS driver development kit...

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
[last_used]
device_uri = hpfax:/net/Officejet_4500_G510g-m?zc=HP6C85A7

[installation]
date_time = 15/01/13 14:45:48
version = 3.12.2



--------------------------
| DISCOVERED USB DEVICES |
--------------------------

No devices found.

---------------------------------
| INSTALLED CUPS PRINTER QUEUES |
---------------------------------


Officejet-4500-G510g-m
----------------------
Type: Unknown
Device URI: dnssd://Officejet%204500%20G510g-m%20%5B6C85A7%5D._pdl-datastream._tcp.local/
PPD: /etc/cups/ppd/Officejet-4500-G510g-m.ppd
PPD Description: HP Officejet 4500 g510g-m, hpcups 3.12.2
Printer status: printer Officejet-4500-G510g-m is idle.  enabled since Tue 15 Jan 2013 14:38:13 CST
	Ready to print.


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

tony adm lp dialout fax cdrom floppy tape audio dip www-data video plugdev fuse lpadmin netdev admin nopasswdlogin sambashare scanner powerdev vboxusers

User member of group 'lp'. Enables print/ scan/ fax.
User member of group 'lpadmin'.

-----------
| SUMMARY |
-----------


Please refer to the installation instructions at:
[http://hplip.sourceforge.net/install/index.html](http://hplip.sourceforge.net/install/index.html)


Done.

Everything looks ok as far as I can tell except the output of sane -L. Any suggestions please?
Thanks

---

