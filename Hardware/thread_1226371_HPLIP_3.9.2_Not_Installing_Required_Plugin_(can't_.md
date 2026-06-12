---
title: "HPLIP 3.9.2 Not Installing Required Plugin? (can't scan)"
date: 2009-07-29
forum: Hardware
---

### Post by mattlach on 2009-07-29
Hey all,

I have a HP HP CM1312 NFI multi function printer.  It works like a dream with HPLIP except that it won't scan.

I have understood that HPLIP needs a plugin (that it installs itself from within the GUI by pressing a button, see below)

[img]http://farm3.static.flickr.com/2657/3769069879_6ce25bb852_o.jpg[/img]

After installing the plugin it is supposed to be able to scan, but whenever I try to scan, I get the following error message:

[img]http://farm4.static.flickr.com/3568/3769077575_da57267e15_o.jpg[/img]

Failed to open device 'hpaio:/net/HP_Color_LaserJet_CM1312nfi_MFP?ip=192.168.1.102': Error during device I/O.

The device works perfectly under Windows, but I am trying to avoid booting in windows whenever possible.

I did some random googling in which it was suggested I run "hp-check -r" to see if all the runtime dependencies check out.  I did this, and it is attached below:

```

HP Linux Imaging and Printing System (ver. 3.9.2)
Dependency/Version Check Utility ver. 14.1

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
Linux matt 2.6.28-13-generic #45-Ubuntu SMP Tue Jun 30 22:12:12 UTC 2009 x86_64 GNU/Linux

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
error: Version: (Not available. CUPS may not be installed or not running.)

Checking for dbus/python-dbus...
dbus daemon is running.
python-dbus version: 0.83.0


------------------------
| RUNTIME DEPENDENCIES |
------------------------


Checking for dependency: CUPS - Common Unix Printing System...
OK, found.

Checking for dependency: CUPS DDK - CUPS driver development kit...
OK, found.

Checking for dependency: GhostScript - PostScript and PDF language interpreter and previewer...
OK, found.

Checking for dependency: PIL - Python Imaging Library (required for commandline scanning with hp-scan)...
OK, found.

Checking for dependency: ppdev - Parallel port support kernel module....
OK, found.

Checking for dependency: PyQt 4- Qt interface for Python (for Qt version 4.x)...
OK, found.

Checking for dependency: PyQt 4 DBus - DBus Support for PyQt4...
OK, found.

Checking for dependency: Python ctypes - A foreign function library for Python...
OK, found.

Checking for dependency: Python DBus - Python bindings for DBus...
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
HPLIP 3.9.2 currently installed in '/usr/share/hplip'.

Current contents of '/etc/hp/hplip.conf' file:
# hplip.conf.  Generated from hplip.conf.in by configure.

[hplip]
version=3.9.2

[dirs]
home=/usr/share/hplip
run=/var/run
ppd=/usr/share/ppd/hpijs/HP
ppdbase=/usr/share/ppd/hpijs
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
foomatic-drv-install=yes
foomatic-ppd-install=no
foomatic-rip-hplip-install=no
internal-tag=3.9.2.49
restricted-build=no
ui-toolkit=qt4
qt3=no
qt4=yes




Current contents of '~/.hplip/hplip.conf' file:
[last_used]
device_uri = hp:/net/HP_Color_LaserJet_CM1312nfi_MFP?ip=192.168.1.102

[installation]
version = 3.9.2.49
date_time = 07/29/09 13:58:19



-------------------------------
| DISCOVERED PARALLEL DEVICES |
-------------------------------

No devices found.

--------------------------
| DISCOVERED USB DEVICES |
--------------------------

No devices found.

---------------------------------
| INSTALLED CUPS PRINTER QUEUES |
---------------------------------

 
Color-LaserJet-CM1312nfi-MFP
----------------------------
Type: Printer
Installed in HPLIP?: Yes, using the hp: CUPS backend.
Device URI: hp:/net/HP_Color_LaserJet_CM1312nfi_MFP?ip=192.168.1.102
PPD: /etc/cups/ppd/Color-LaserJet-CM1312nfi-MFP.ppd
PPD Description: HP Color LaserJet cm1312nfi MFP hpijs, 3.9.2
Printer status: printer Color-LaserJet-CM1312nfi-MFP is idle.  enabled since Wed 08 Jul 2009 11:24:18 PM EDT
error: Required plug-in status: Not installed
Communication status: Good


----------------------
| SANE CONFIGURATION |
----------------------

'hpaio' in '/etc/sane.d/dll.conf'...
'hpaio' in '/etc/sane.d/dll.d/hplip'...
OK, found. SANE backend 'hpaio' is properly set up.

Checking output of 'scanimage -L'...
device `hpaio:/net/HP_Color_LaserJet_CM1312nfi_MFP?ip=192.168.1.102' is a Hewlett-Packard HP_Color_LaserJet_CM1312nfi_MFP all-in-one


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
 
-----------
| SUMMARY |
-----------

error: 2 errors and/or warnings.

Please refer to the installation instructions at:
http://hplip.sourceforge.net/install/index.html


Done.
```

AS you can see it is complaining that the required plugin is not installed, even though I installed it from the gui....

At first I thought it may be a permissions thing (as in the user account not having sufficient permissions to write the plugin to its proper place), but the hplip gui does ask for the root password when installing the plugin, so it can't be that right?

Any suggestions greatly appreciated!

---

### Post by mattlach on 2009-07-29
Looks like I found the answer in this bug report:

[https://bugs.launchpad.net/hplip/+bug/405864](https://bugs.launchpad.net/hplip/+bug/405864)

They have applied a patch for hplip 3.9.8 (which has not been released yet)

Does anyone know if I can manually install the plugin to make it work in the mean time?

---

### Post by mattlach on 2009-07-29
Hmm..

I ran hp-plugin in interactive mode (-i) after enabling the root account, and it still didn't work.

I then copied the download link for the plugin ([http://www.linuxprinting.org/download/printdriver/auxfiles/HP/plugins/hplip-3.9.2-plugin.run](http://www.linuxprinting.org/download/printdriver/auxfiles/HP/plugins/hplip-3.9.2-plugin.run)) from the interactive mode, downloaded it with wget and executed it.

Output was as follows:

```

Verifying archive integrity... All good.
Uncompressing HPLIP 3.9.2 Plugin Self Extracting Archive................................

HP Linux Imaging and Printing System (ver. 3.9.2)
Plugin Installer ver. 2.0

Copyright (c) 2001-9 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.


HP Linux Imaging and Printing System (ver. 3.9.2)
Plugin Installer ver. 2.0

Copyright (c) 2001-8 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

Plug-in version: 3.9.2
Installed HPLIP version: 3.9.2
Number of files to install: 27

QGtkStyle cannot be used together with the GTK_Qt engine.
Qt: Session management error: None of the authentication protocols specified are supported
Starting plugin install...
Copying file 86-hpmud-hp_laserjet_1000.rules to /etc/udev/rules.d/86-hpmud-hp_laserjet_1000.rules...
Copying file 86-hpmud-hp_laserjet_1005_series.rules to /etc/udev/rules.d/86-hpmud-hp_laserjet_1005_series.rules...
Copying file 86-hpmud-hp_laserjet_1018.rules to /etc/udev/rules.d/86-hpmud-hp_laserjet_1018.rules...
Copying file 86-hpmud-hp_laserjet_1020.rules to /etc/udev/rules.d/86-hpmud-hp_laserjet_1020.rules...
Copying file 86-hpmud-hp_laserjet_p1005.rules to /etc/udev/rules.d/86-hpmud-hp_laserjet_p1005.rules...
Copying file 86-hpmud-hp_laserjet_p1006.rules to /etc/udev/rules.d/86-hpmud-hp_laserjet_p1006.rules...
Copying file 86-hpmud-hp_laserjet_p1007.rules to /etc/udev/rules.d/86-hpmud-hp_laserjet_p1007.rules...
Copying file 86-hpmud-hp_laserjet_p1008.rules to /etc/udev/rules.d/86-hpmud-hp_laserjet_p1008.rules...
Copying file 86-hpmud-hp_laserjet_p1505.rules to /etc/udev/rules.d/86-hpmud-hp_laserjet_p1505.rules...
Copying file bb_marvell-x86_64.so to /usr/share/hplip/scan/plugins/bb_marvell-x86_64.so (link=/usr/share/hplip/scan/plugins/bb_marvell.so)...
Creating symlink /usr/share/hplip/scan/plugins/bb_marvell.so (link) to file /usr/share/hplip/scan/plugins/bb_marvell-x86_64.so (target)...
Copying file bb_soap-x86_64.so to /usr/share/hplip/scan/plugins/bb_soap-x86_64.so (link=/usr/share/hplip/scan/plugins/bb_soap.so)...
Creating symlink /usr/share/hplip/scan/plugins/bb_soap.so (link) to file /usr/share/hplip/scan/plugins/bb_soap-x86_64.so (target)...
Copying file bb_soapht-x86_64.so to /usr/share/hplip/scan/plugins/bb_soapht-x86_64.so (link=/usr/share/hplip/scan/plugins/bb_soapht.so)...
Creating symlink /usr/share/hplip/scan/plugins/bb_soapht.so (link) to file /usr/share/hplip/scan/plugins/bb_soapht-x86_64.so (target)...
Copying file hp_laserjet_1000.fw.gz to /usr/share/hplip/data/firmware/hp_laserjet_1000.fw.gz...
Copying file hp_laserjet_1005_series.fw.gz to /usr/share/hplip/data/firmware/hp_laserjet_1005_series.fw.gz...
Copying file hp_laserjet_1018.fw.gz to /usr/share/hplip/data/firmware/hp_laserjet_1018.fw.gz...
Copying file hp_laserjet_1020.fw.gz to /usr/share/hplip/data/firmware/hp_laserjet_1020.fw.gz...
Copying file hp_laserjet_p1005.fw.gz to /usr/share/hplip/data/firmware/hp_laserjet_p1005.fw.gz...
Copying file hp_laserjet_p1006.fw.gz to /usr/share/hplip/data/firmware/hp_laserjet_p1006.fw.gz...
Copying file hp_laserjet_p1007.fw.gz to /usr/share/hplip/data/firmware/hp_laserjet_p1007.fw.gz...
Copying file hp_laserjet_p1008.fw.gz to /usr/share/hplip/data/firmware/hp_laserjet_p1008.fw.gz...
Copying file hp_laserjet_p1505.fw.gz to /usr/share/hplip/data/firmware/hp_laserjet_p1505.fw.gz...
Copying file license.txt to /usr/share/hplip/data/plugins/license.txt...
Copying file lj-x86_64.so to /usr/share/hplip/prnt/plugins/lj-x86_64.so (link=/usr/share/hplip/prnt/plugins/lj.so)...
Creating symlink /usr/share/hplip/prnt/plugins/lj.so (link) to file /usr/share/hplip/prnt/plugins/lj-x86_64.so (target)...
Setting plugin installed flag to 1.


Done.

```

However, hp-check still outputs "required plugin not installed" and any attempt to scan fails.

I also couldn't help but notice that none of the filenames installed in the plugin executable matched my printer model....   The hplip web page says that scanning should be supported with the required plugin, however.

I am at a loss...

---

### Post by mattlach on 2009-07-29
> **mattlach said:**
> Looks like I found the answer in this bug report:

[https://bugs.launchpad.net/hplip/+bug/405864](https://bugs.launchpad.net/hplip/+bug/405864)

They have applied a patch for hplip 3.9.8 (which has not been released yet)

Does anyone know if I can manually install the plugin to make it work in the mean time?

Appears as if this bug is incorrect after all.  It speaks to file not executing.   It appears to be executing fine and copying the driver files, however - hp-check still complains of driver not being installed and scanning still does not work.

I've exhausted my limited abilities in trouble shooting this.  I think it may be time for a bug report.

---

### Post by mattlach on 2009-07-29
Bug reported [here](https://bugs.launchpad.net/ubuntu/+source/hplip/+bug/406570).

---

