---
title: "Setting up a new HP Printer Fax and I forgot how."
date: 2021-01-14
forum: Hardware
---

### Post by rsteinmetz70112 on 2021-01-14
I'm setting up a new HP Printer/Scanner/Fax on an Ubuntu 20.04.1 LTS compyer. 
HP Model is HP_ENVY_Photo_7800_series

The Printer is working
The Scanner is working
But I want the fax to work and I can't get it to set up properly.

I ran:
```
hp-check -r
```

It reported:
```

Missing Required Dependencies
-----------------------------
error: 'libcups2' package is missing/incompatible 
error: 'python3-pyqt4' package is missing/incompatible 
error: 'gtk2-engines-pixbuf' package is missing/incompatible 

Missing Optional Dependencies
-----------------------------
error: 'python3-dbus.mainloop.qt' package is missing/incompatible 
```

Ubuntu either reports the packages are installed and the latest or there is not such package availible.

The HP Address books seems installed and working.
The HP ToolBox seems installed and working but reports no HP devices installed.
IF I try to set the device up it seems to set up the queues, but the printer doesn;,t work, although the CUPS printers still work.
CUPS seems to have installed the printer automatically.
The HP Fax Utility doesn't start.
I need to get the fax working anybody got some pointers?

---

### Post by yancek on 2021-01-15
The link below has the manual for the machine you are using and in Section 5, instructions for the Fax part of it.

[http://h10032.www1.hp.com/ctg/Manual/c05634824](http://h10032.www1.hp.com/ctg/Manual/c05634824)

The HP Support site for that hardware is at the link below/

[https://support.hp.com/us-en/printer-setup/hp-envy-photo-7800-all-in-one-printer-series/9073159](https://support.hp.com/us-en/printer-setup/hp-envy-photo-7800-all-in-one-printer-series/9073159)

More info on drivers for HP printers on Linux.

[https://developers.hp.com/hp-linux-imaging-and-printing/](https://developers.hp.com/hp-linux-imaging-and-printing/)

---

### Post by rsteinmetz70112 on 2021-01-15
Thanks,
Unfortunately I have all of that and HPLIP is installed. The Printer and Scanner work just fine but I can't get the FAX printer to work. CUPS sens a fine to the printer queue but the fax interface never opens.

---

### Post by rsteinmetz70112 on 2021-01-16
OK I ran hp-check and got this:

```
$ hp-check
hp-check -i
Saving output in log file: /home/debbie/hp-check.log

HP Linux Imaging and Printing System (ver. 3.20.3)
Dependency/Version Check Utility ver. 15.1

Copyright (c) 2001-18 HP Development Company, LP
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

Check types:                                                                    
a. EXTERNALDEP - External Dependencies                                          
b. GENERALDEP - General Dependencies (required both at compile and run time)    
c. COMPILEDEP - Compile time Dependencies                                       
d. [All are run-time checks]                                                    
PYEXT SCANCONF QUEUES PERMISSION                                                

Status Types:
    OK
    MISSING       - Missing Dependency or Permission or Plug-in
    INCOMPAT      - Incompatible dependency-version or Plugin-version

warning: ubuntu-20.04 version is not supported. Using ubuntu-19.10 versions dependencies to verify and install...

---------------
| SYSTEM INFO |
---------------

 Kernel: 5.4.0-62-generic #70-Ubuntu SMP Tue Jan 12 12:45:47 UTC 2021 GNU/Linux
 Host: apartment
 Proc: 5.4.0-62-generic #70-Ubuntu SMP Tue Jan 12 12:45:47 UTC 2021 GNU/Linux
 Distribution: ubuntu 20.04
 Bitness: 64 bit


-----------------------
| HPLIP CONFIGURATION |
-----------------------

HPLIP-Version: HPLIP 3.20.3
HPLIP-Home: /usr/share/hplip
warning: HPLIP-Installation: Auto installation is not supported for ubuntu distro  20.04 version 

Current contents of '/etc/hp/hplip.conf' file:
# hplip.conf.  Generated from hplip.conf.in by configure.

[hplip]
version=3.20.3

[dirs]
home=/usr/share/hplip
run=/var/run
ppd=/usr/share/ppd/hplip/HP
ppdbase=/usr/share/ppd/hplip
doc=/usr/share/doc/hplip
html=/usr/share/doc/hplip-doc
icon=no
cupsbackend=/usr/lib/cups/backend
cupsfilter=/usr/lib/cups/filter
drv=/usr/share/cups/drv
bin=/usr/bin
apparmor=/etc/apparmor.d
# Following values are determined at configure time and cannot be changed.
[configure]
network-build=yes
libusb01-build=no
pp-build=no
gui-build=yes
scanner-build=yes
fax-build=yes
dbus-build=yes
cups11-build=no
doc-build=yes
shadow-build=no
hpijs-install=yes
foomatic-drv-install=yes
foomatic-ppd-install=no
foomatic-rip-hplip-install=no
hpcups-install=yes
cups-drv-install=yes
cups-ppd-install=no
internal-tag=3.20.3
restricted-build=no
ui-toolkit=qt5
qt3=no
qt4=no
qt5=yes
policy-kit=yes
lite-build=no
udev_sysfs_rules=no
hpcups-only-build=no
hpijs-only-build=no
apparmor_build=no
class-driver=no


Current contents of '/var/lib/hp/hplip.state' file:
Plugins are not installed. Could not access file: No such file or directory

Current contents of '~/.hplip/hplip.conf' file:
[commands]
scan = /usr/bin/simple-scan %SANE_URI%

[fax]
email_address = 
voice_phone = 

[last_used]
device_uri = "hpfax:/net/ENVY_Photo_7800_series?ip=192.168.0.64"
printer_name = 
working_dir = .

[polling]
device_list = 
enable = false
interval = 5

[refresh]
enable = false
rate = 30
type = 1

[settings]
systray_messages = 0
systray_visible = 0

[upgrade]
last_upgraded_time = 1505675819
notify_upgrade = false
pending_upgrade_time = 0

[installation]
date_time = 01/16/21 15:31:39
version = 3.20.3


 <Package-name>        <Package-Desc>      <Required/Optional> <Min-Version> <Installed-Version> <Status>   <Comment>

-------------------------
| External Dependencies |
-------------------------

 error: cups          CUPS - Common Unix Printing System                           REQUIRED        1.1             -               INCOMPAT   'CUPS may not be installed or not running'
 gs                   GhostScript - PostScript and PDF language interpreter and previewer REQUIRED        7.05            9.50            OK         -
 xsane                xsane - Graphical scanner frontend for SANE                  OPTIONAL        0.9             0.999           OK         -
 scanimage            scanimage - Shell scanning program                           OPTIONAL        1.0             1.0.29          OK         -
 dbus                 DBus - Message bus system                                    REQUIRED        -               1.12.16         OK         -
 policykit            PolicyKit - Administrative policy framework                  OPTIONAL        -               0.105           OK         -
 network              network -wget                                                OPTIONAL        -               1.20.3          OK         -
 avahi-utils          avahi-utils                                                  OPTIONAL        -               0.7             OK         -

------------------------
| General Dependencies |
------------------------

 libjpeg              libjpeg - JPEG library                                       REQUIRED        -               -               OK         -
 cups-devel           CUPS devel- Common Unix Printing System development files    REQUIRED        -               -               OK         -
 cups-image           CUPS image - CUPS image development files                    REQUIRED        -               -               OK         -
 libpthread           libpthread - POSIX threads library                           REQUIRED        -               b'2.31'         OK         -
 libusb               libusb - USB library                                         REQUIRED        -               1.0             OK         -
 sane                 SANE - Scanning library                                      REQUIRED        -               -               OK         -
 sane-devel           SANE - Scanning library development files                    REQUIRED        -               -               OK         -
 libnetsnmp-devel     libnetsnmp-devel - SNMP networking library development files REQUIRED        5.0.9           5.8             OK         -
 libcrypto            libcrypto - OpenSSL cryptographic library                    REQUIRED        -               1.1.1           OK         -
 python3X             Python 2.2 or greater - Python programming language          REQUIRED        2.2             3.8.5           OK         -
 python3-notify2      Python libnotify - Python bindings for the libnotify Desktop notifications OPTIONAL        -               -               OK         -
 error: python3-pyqt4-dbus PyQt 4 DBus - DBus Support for PyQt4                         OPTIONAL        4.0             -               MISSING    'python3-pyqt4-dbus needs to be installed'
 error: python3-pyqt4 PyQt 4- Qt interface for Python (for Qt version 4.x)         REQUIRED        4.0             -               MISSING    'python3-pyqt4 needs to be installed'
 python3-dbus         Python DBus - Python bindings for DBus                       REQUIRED        0.80.0          1.2.16          OK         -
 python3-xml          Python XML libraries                                         REQUIRED        -               2.2.9           OK         -
 python3-devel        Python devel - Python development files                      REQUIRED        2.2             3.8.5           OK         -
 python3-pil          PIL - Python Imaging Library (required for commandline scanning with hp-scan) OPTIONAL        -               7.0.0           OK         -
 python3-reportlab    Reportlab - PDF library for Python                           OPTIONAL        2.0             3.5.34          OK         -

--------------
| COMPILEDEP |
--------------

 libtool              libtool - Library building support services                  REQUIRED        -               2.4.6           OK         -
 gcc                  gcc - GNU Project C and C++ Compiler                         REQUIRED        -               9.3.0           OK         -
 make                 make - GNU make utility to maintain groups of programs       REQUIRED        3.0             4.2.1           OK         -

---------------------
| Python Extentions |
---------------------

 cupsext              CUPS-Extension                                               REQUIRED        -               3.20.3          OK         -
 hpmudext             IO-Extension                                                 REQUIRED        -               3.20.3          OK         -

----------------------
| Scan Configuration |
----------------------

'/etc/sane.d/dll.d/hpaio' not found.
 hpaio                HPLIP-SANE-Backend                                           REQUIRED        -               3.20.3          OK         'hpaio found in /etc/sane.d/dll.conf'
 scanext              Scan-SANE-Extension                                          REQUIRED        -               3.20.3          OK         -

------------------------------
| DISCOVERED SCANNER DEVICES |
------------------------------

device `hpaio:/usb/ENVY_Photo_7800_series?serial=TH8828V0VX' is a Hewlett-Packard ENVY_Photo_7800_series all-in-one
device `hpaio:/net/ENVY_Photo_7800_series?ip=192.168.0.64' is a Hewlett-Packard ENVY_Photo_7800_series all-in-one


--------------------------
| DISCOVERED USB DEVICES |
--------------------------

  Device URI                        Model                    
  --------------------------------  -------------------------
  hp:/usb/ENVY_Photo_7800_series?s  HP ENVY Photo 7800 series
  erial=TH8828V0VX                                           

---------------------------------
| INSTALLED CUPS PRINTER QUEUES |
---------------------------------

 
ENVY_Photo_7800
---------------
Type: Printer
Device URI: hp:/usb/ENVY_Photo_7800_series?serial=TH8828V0VX
PPD: /etc/cups/ppd/ENVY_Photo_7800.ppd
warning: Failed to read /etc/cups/ppd/ENVY_Photo_7800.ppd ppd file
PPD Description: 
Printer status: printer ENVY_Photo_7800 is idle.  enabled since Sat 16 Jan 2021 03:08:17 PM EST
Communication status: Good

ENVY_Photo_7800_2
-----------------
Type: Printer
Device URI: hp:/net/ENVY_Photo_7800_series?ip=192.168.0.64
PPD: /etc/cups/ppd/ENVY_Photo_7800_2.ppd
warning: Failed to read /etc/cups/ppd/ENVY_Photo_7800_2.ppd ppd file
PPD Description: 
Printer status: printer ENVY_Photo_7800_2 now printing ENVY_Photo_7800_2-554.  enabled sProcessing page 1... 02:15:59 PM EST
error: Unable to communicate with device (code=12): hp:/net/ENVY_Photo_7800_series?ip=192.168.0.64
error: unable to open channel
error: Communication status: Failed

ENVY_Photo_7800_fax
-------------------
Type: Fax
Device URI: hpfax:/usb/ENVY_Photo_7800_series?serial=TH8828V0VX
PPD: /etc/cups/ppd/ENVY_Photo_7800_fax.ppd
warning: Failed to read /etc/cups/ppd/ENVY_Photo_7800_fax.ppd ppd file
PPD Description: 
Printer status: printer ENVY_Photo_7800_fax is idle.  enabled since Sat 16 Jan 2021 01:58:54 PM EST
Communication status: Good

ENVY_Photo_7800_fax_2
---------------------
Type: Fax
Device URI: hpfax:/net/ENVY_Photo_7800_series?ip=192.168.0.64
PPD: /etc/cups/ppd/ENVY_Photo_7800_fax_2.ppd
warning: Failed to read /etc/cups/ppd/ENVY_Photo_7800_fax_2.ppd ppd file
PPD Description: 
Printer status: printer ENVY_Photo_7800_fax_2 is idle.  enabled since Sat 16 Jan 2021 01:51:46 PM EST
error: Unable to communicate with device (code=12): hpfax:/net/ENVY_Photo_7800_series?ip=192.168.0.64
error: unable to open channel
error: Communication status: Failed

Epson-Stylus-Color-860
----------------------
Type: Unknown
Device URI: socket://192.168.2.252:9100
PPD: /etc/cups/ppd/Epson-Stylus-Color-860.ppd
warning: Failed to read /etc/cups/ppd/Epson-Stylus-Color-860.ppd ppd file
PPD Description: 
Printer status: printer Epson-Stylus-Color-860 is idle.  enabled since Wed 16 Dec 2020 04:56:13 PM EST
warning: Printer is not HPLIP installed. Printers must use the hp: or hpfax: CUPS backend for HP-Devices.

HP-LaserJet-2100-2
------------------
Type: Unknown
Device URI: socket://192.168.0.251
PPD: /etc/cups/ppd/HP-LaserJet-2100-2.ppd
warning: Failed to read /etc/cups/ppd/HP-LaserJet-2100-2.ppd ppd file
PPD Description: 
Printer status: printer HP-LaserJet-2100-2 is idle.  enabled since Sat 16 Jan 2021 12:16:34 PM EST
warning: Printer is not HPLIP installed. Printers must use the hp: or hpfax: CUPS backend for HP-Devices.


--------------
| PERMISSION |
--------------

USB             ENVY_Photo_7800                Required        -        -        OK       Node:'/dev/bus/usb/001/003' Perm:'  root  lp rw- rw- rw- rw- r--'
 
-----------
| SUMMARY |
-----------

Missing Required Dependencies
-----------------------------
error: 'libcups2' package is missing/incompatible 
error: 'python3-pyqt4' package is missing/incompatible 
error: 'gtk2-engines-pixbuf' package is missing/incompatible 

Missing Optional Dependencies
-----------------------------
error: 'python3-dbus.mainloop.qt' package is missing/incompatible 

Total Errors: 5
Total Warnings: 2


Done.
debbie@apartment:~$ 
HP Linux Imaging and Printing System (ver. 3.20.3)
Fax Address Book ver. 6.0

Copyright (c) 2001-18 HP Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.
```

OF the packages listed as missing or incompatable:

libcups2 is the latest version

The others are not in the repositories.
HPLIP is shown as the latest from the repositories and no packages are shown as broken or partially installed.

---

### Post by rsteinmetz70112 on 2021-01-16
e```
rror: cups          CUPS - Common Unix Printing System                           REQUIRED        1.1             -               INCOMPAT   'CUPS may not be installed or not running'
cups is already the newest version (2.3.1-9ubuntu1.1).
```
```
error: python3-pyqt4-dbus PyQt 4 DBus - DBus Support for PyQt4                         OPTIONAL        4.0             -               MISSING    'python3-pyqt4-dbus needs to be installed'
E: Unable to locate package python3-pyqt4-dbus
```
```
error: python3-pyqt4 PyQt 4- Qt interface for Python (for Qt version 4.x)         REQUIRED        4.0             -               MISSING    'python3-pyqt4 needs to be installed'
E: Unable to locate package python3-pyqt4
```
```
/etc/sane.d/dll.d/hpaio
/etc/sane.d/dll.d# ls -ld *
-rw-r--r-- 1 root root 38 Mar 29  2016 hplip
hpaio                HPLIP-SANE-Backend                                           REQUIRED        -               3.20.3          OK         'hpaio found in /etc/sane.d/dll.conf
```

```
warning: Failed to read /etc/cups/ppd/ENVY_Photo_7800.ppd ppd file
/etc/cups/ppd# ls -ld *
-rw-r----- 1 root lp  31541 Jan 14 21:03 ENVY_Photo_7800_2.ppd
-rw-r----- 1 root lp   2651 Jan 14 21:03 ENVY_Photo_7800_fax_2.ppd
-rw-r----- 1 root lp   2651 Jan 16 13:58 ENVY_Photo_7800_fax.ppd
-rw-r----- 1 root lp  31541 Jan 16 13:58 ENVY_Photo_7800.ppd
-rw-r----- 1 root lp 160516 Nov  9 22:06 Epson-Stylus-Color-860.ppd
-rw-r----- 1 root lp 172230 Oct 20  2018 Epson-Stylus-Color-860.ppd.O
-rw-r----- 1 root lp  19941 Nov  9 22:05 HP-LaserJet-2100-2.ppd
-rw-r----- 1 root lp  19941 Oct 17  2019 HP-LaserJet-2100-2.ppd.O
```

```
Printer status: printer ENVY_Photo_7800_2 now printing ENVY_Photo_7800_2-554.  enabled sProcessing page 1... 02:15:59 PM EST
error: Unable to communicate with device (code=12): hp:/net/ENVY_Photo_7800_series?ip=192.168.0.64
error: unable to open channel
error: Communication status: Failed
```

```
PPD: /etc/cups/ppd/ENVY_Photo_7800_fax.ppd
warning: Failed to read /etc/cups/ppd/ENVY_Photo_7800_fax.ppd ppd file
```
```
PPD Description: 
Printer status: printer ENVY_Photo_7800_fax is idle.  enabled since Sat 16 Jan 2021 01:58:54 PM EST
Communication status: Good
```

```
error: 'libcups2' package is missing/incompatible 
error: error: 'libcups2' package is missing/incompatible 
error: 'python3-pyqt4' package is missing/incompatible 
error: 'gtk2-engines-pixbuf' package is missing/incompatible 

Missing Optional Dependencies
-----------------------------
error: 'python3-dbus.mainloop.qt' package is missing/incompatible package is missing/incompatible 
error: 'gtk2-engines-pixbuf' package is missing/incompatible 

```

Obviously something is wrong, Apparently eithe the hp utilities are incorrect ot there are missing dependancies.

---

### Post by rsteinmetz70112 on 2021-01-18
After noodling around the Internet and Launchpad, it seems HPLIP is not really ready for 20.04 LTS as the default version of Python doesn't match and the dependencies are apparently not correctly configured it. The Printer function works the Scanner function works but the fax function doesn't work. I also keep getting USB communication errors.

---

