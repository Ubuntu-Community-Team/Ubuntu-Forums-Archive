---
title: "Cannoct connect to HP5510 &quot; unable to open device&quot;"
date: 2016-09-30
forum: Hardware
---

### Post by pecoflyer on 2016-09-30
Hello
I use Xubuntu 16.04 and installed HPLIP and HPLIP Toolbox to connect to a HP5510 printer.

I ran hp-check as you can see. All seems OK except the CUPS queue which returns " unable to open device".

I am working from a Desktop PC connected with UTP to Router1, itself connected to Router2 ( also via UTP) which in turn is connected via Wi Fi to the printer.

Ping is OK

What should I try next?

Any help much appreciated

```


pecoflyer@PCDAD-UP:~$ hp-check -t
Saving output in log file: /home/pecoflyer/hp-check.log

HP Linux Imaging and Printing System (ver. 3.16.3)
Dependency/Version Check Utility ver. 15.1

Copyright (c) 2001-15 HP Development Company, LP
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

 
---------------
| SYSTEM INFO |
---------------

 Kernel: 4.4.0-36-generic #55-Ubuntu SMP Thu Aug 11 18:01:55 UTC 2016 GNU/Linux
 Host: PCDAD-UP
 Proc: 4.4.0-36-generic #55-Ubuntu SMP Thu Aug 11 18:01:55 UTC 2016 GNU/Linux
 Distribution: ubuntu 16.04
 Bitness: 64 bit


-----------------------
| HPLIP CONFIGURATION |
-----------------------

HPLIP-Version: HPLIP 3.16.3
HPLIP-Home: /usr/share/hplip
HPLIP-Installation: Auto installation is supported for ubuntu distro  16.04 version 

Current contents of '/etc/hp/hplip.conf' file:
# hplip.conf.  Generated from hplip.conf.in by configure.

[hplip]
version=3.16.3

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
internal-tag=3.16.3
restricted-build=no
ui-toolkit=qt4
qt3=no
qt4=yes
policy-kit=yes
lite-build=no
udev_sysfs_rules=no
hpcups-only-build=no
hpijs-only-build=no
apparmor_build=no


Current contents of '/var/lib/hp/hplip.state' file:
[plugin]
installed = 1
eula = 1
version = 3.16.3



Current contents of '~/.hplip/hplip.conf' file:
[settings]
systray_visible = 0
systray_messages = 0

[last_used]
device_uri = "hp:/net/Photosmart_5510_series?ip=192.168.0.212"
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

[upgrade]
notify_upgrade = false
last_upgraded_time = 1475131009
pending_upgrade_time = 0

[installation]
date_time = 09/30/16 12:05:44
version = 3.16.3


 <Package-name>        <Package-Desc>      <Required/Optional> <Min-Version> <Installed-Version> <Status>   <Comment>

--------------------------
|  External Dependencies |
--------------------------

 policykit            PolicyKit - Administrative policy framework                  OPTIONAL        -               0.105           OK         -
 gs                   GhostScript - PostScript and PDF language interpreter and previewer REQUIRED        7.05            9.18            OK         -
 avahi-utils          avahi-utils                                                  OPTIONAL        -               0.6.32          OK         -
 dbus                 DBus - Message bus system                                    REQUIRED        -               1.10.6          OK         -
 cups                 CUPS - Common Unix Printing System                           REQUIRED        1.1             2.1.3           OK         'CUPS Scheduler is running'
 network              network -wget                                                OPTIONAL        -               1.17.1          OK         -
 scanimage            scanimage - Shell scanning program                           OPTIONAL        1.0             1.0.25          OK         -
 xsane                xsane - Graphical scanner frontend for SANE                  OPTIONAL        0.9             0.999           OK         -

-------------------------
|  General Dependencies |
-------------------------

 sane                 SANE - Scanning library                                      REQUIRED        -               1.0.25          OK         -
 python3-devel        Python devel - Python development files                      REQUIRED        2.2             3.5.2           OK         -
 libusb               libusb - USB library                                         REQUIRED        -               1.0             OK         -
 python3-xml          Python XML libraries                                         REQUIRED        -               2.1.0           OK         -
 cups-image           CUPS image - CUPS image development files                    REQUIRED        -               2.1.3           OK         -
 sane-devel           SANE - Scanning library development files                    REQUIRED        -               1.0.25          OK         -
 python3-pil          PIL - Python Imaging Library (required for commandline scanning with hp-scan) OPTIONAL        -               1.1.7           OK         -
 cups-devel           CUPS devel- Common Unix Printing System development files    REQUIRED        -               2.1.3           OK         -
 libcrypto            libcrypto - OpenSSL cryptographic library                    REQUIRED        -               1.0.2           OK         -
 libnetsnmp-devel     libnetsnmp-devel - SNMP networking library development files REQUIRED        5.0.9           5.7.3           OK         -
 python3-reportlab    Reportlab - PDF library for Python                           OPTIONAL        2.0             3.3.0           OK         -
 libjpeg              libjpeg - JPEG library                                       REQUIRED        -               -               OK         -
 python3X             Python 2.2 or greater - Python programming language          REQUIRED        2.2             3.5.2           OK         -
 python3-notify2      Python libnotify - Python bindings for the libnotify Desktop notifications OPTIONAL        -               -               OK         -
 python3-dbus         Python DBus - Python bindings for DBus                       REQUIRED        0.80.0          1.2.0           OK         -
 libpthread           libpthread - POSIX threads library                           REQUIRED        -               b'2.23'         OK         -
 python3-pyqt4        PyQt 4- Qt interface for Python (for Qt version 4.x)         REQUIRED        4.0             4.11.4          OK         -
 python3-pyqt4-dbus   PyQt 4 DBus - DBus Support for PyQt4                         OPTIONAL        4.0             4.11.4          OK         -

---------------
|  COMPILEDEP |
---------------

 libtool              libtool - Library building support services                  REQUIRED        -               2.4.6           OK         -
 gcc                  gcc - GNU Project C and C++ Compiler                         REQUIRED        -               5.4.0           OK         -
 make                 make - GNU make utility to maintain groups of programs       REQUIRED        3.0             4.1             OK         -

----------------------
|  Python Extentions |
----------------------

 cupsext              CUPS-Extension                                               REQUIRED        -               3.16.3          OK         -
 hpmudext             IO-Extension                                                 REQUIRED        -               3.16.3          OK         -

-----------------------
|  Scan Configuration |
-----------------------

 scanext              Scan-SANE-Extension                                          REQUIRED        -               3.16.3          OK         -
'/etc/sane.d/dll.d/hpaio' not found.
 hpaio                HPLIP-SANE-Backend                                           REQUIRED        -               3.16.3          OK         'hpaio found in /etc/sane.d/dll.conf'

-----------------------
|  Other Dependencies |
-----------------------


------------------------------
| DISCOVERED SCANNER DEVICES |
------------------------------

device `hpaio:/net/Photosmart_5510_series?ip=192.168.0.212' is a Hewlett-Packard Photosmart_5510_series all-in-one


--------------------------
| DISCOVERED USB DEVICES |
--------------------------

No devices found.

---------------------------------
| INSTALLED CUPS PRINTER QUEUES |
---------------------------------

 
Photosmart_5510
---------------
Type: Printer
Device URI: hp:/net/Photosmart_5510_series?ip=192.168.0.212
PPD: /etc/cups/ppd/Photosmart_5510.ppd
PPD Description: HP Photosmart 5510 Series, hpcups 3.16.3
Printer status: printer Photosmart_5510 is idle.  enabled since ven 30 sep 2016 12:01:06Rendering completed
error: Unable to communicate with device (code=12): hp:/net/Photosmart_5510_series?ip=192.168.0.212
error: unable to open channel
error: Communication status: Failed


--------------
| PERMISSION |
--------------

 
-----------
| SUMMARY |
-----------

Missing Required Dependencies
-----------------------------
None

Missing Optional Dependencies
-----------------------------
None


Total Errors: 1
Total Warnings: 0


Done.
pecoflyer@PCDAD-UP:~$ 



```

---

