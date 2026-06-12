---
title: "Problem installing HP Photosmart 5524 on Trusty"
date: 2015-08-03
forum: Hardware
---

### Post by billy_harris2 on 2015-08-03
Hi there:

I'm struggling to set up my printer on Ubuntu. I'm running Ubuntu 14.04 minimal install with Openbox / Tint2, and my printer is an HP Photosmart 5524. I am using hplip 3.15.7 (downloaded from HP website, as apparently the bundled version does not support my device).

I have set it up with hp-setup, which seemed to work okay. I ran hp-check, which threw a few errors until I installed the required missing dependencies and added a line to my /etc/sane.d/dll.conf. It now says there are no errors so far as I can see.

Simplescan detects the scanner and works fine, but the printer will not print, whether from Libreoffice, or using lp and hp-print; test pages also do not print. I have tried sudo lp and sudo hp-print also (thinking it might have to do with permissions), but this does not work either. Bizarrely, the hp-align tool *does* work, including printing an alignment page to scan. This is the only thing I can get it to print.

Checking the print queue with hp-toolbox shows the items in the print queue as on hold, but I can't see a way to get them to print.

Has anyone experienced anything similar or have any suggestions as to a way forward? I have pasted in some diagnostic info below in case it's useful.

Thanks,

Billy.


_**Diagnostics **_
Groups: billy adm cdrom sudo dip plugdev lpadmin sambashare scanner saned

lsusb extract:
Bus 001 Device 003: ID 03f0:e207 Hewlett-Packard 
Bus 001 Device 004: ID 03f0:b111 Hewlett-Packard

```


---------------
| SYSTEM INFO |
---------------

 Kernel: 3.13.0-61-generic #100-Ubuntu SMP Wed Jul 29 11:21:34 UTC 2015 GNU/Linux 
 Host: mutley 
 Proc: 3.13.0-61-generic #100-Ubuntu SMP Wed Jul 29 11:21:34 UTC 2015 GNU/Linux 
 Distribution: ubuntu 14.04
 Bitness: 64 bit


-----------------------
| HPLIP CONFIGURATION |
-----------------------

HPLIP-Version: HPLIP 3.15.7
HPLIP-Home: /usr/share/hplip
HPLIP-Installation: Auto installation is supported for ubuntu distro  14.04 version 

Current contents of '/etc/hp/hplip.conf' file:
# hplip.conf.  Generated from hplip.conf.in by configure.

[hplip]
version=3.15.7

[dirs]
home=/usr/share/hplip
run=/var/run
ppd=/usr/share/ppd/HP
ppdbase=/usr/share/ppd
doc=/usr/share/doc/hplip-3.15.7
html=/usr/share/doc/hplip-3.15.7
icon=/usr/share/applications
cupsbackend=/usr/lib/cups/backend
cupsfilter=/usr/lib/cups/filter
drv=/usr/share/cups/drv/hp
bin=/usr/bin

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
hpijs-install=no
foomatic-drv-install=no
foomatic-ppd-install=no
foomatic-rip-hplip-install=no
hpcups-install=yes
cups-drv-install=yes
cups-ppd-install=no
internal-tag=3.15.7
restricted-build=no
ui-toolkit=qt4
qt3=no
qt4=yes
policy-kit=no
lite-build=no
udev_sysfs_rules=no
hpcups-only-build=no
hpijs-only-build=no


Current contents of '/var/lib/hp/hplip.state' file:
Plugins are not installed. Could not access file: No such file or directory

Current contents of '~/.hplip/hplip.conf' file
[upgrade]
notify_upgrade = true
last_upgraded_time = 1438546143
pending_upgrade_time = 0
latest_available_version = 3.15.7

[settings]
systray_visible = 0
systray_messages = 0

[last_used]
device_uri = "hp:/usb/Photosmart_5520_series?serial=CN346140J00602"
printer_name = Photosmart_5520
working_dir = .

[commands]
scan = /usr/bin/xsane -V %SANE_URI%

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

[installation]
date_time = 03/08/15 20:53:22
version = 3.15.7


 <Package-name>        <Package-Desc>      <Required/Optional> <Min-Version> <Installed-Version> <Status>   <Comment>

--------------------------
|  External Dependencies |
--------------------------

 gs                   GhostScript - PostScript and PDF language interpreter and previewer REQUIRED        7.05            9.10            OK         -
 scanimage            scanimage - Shell scanning program                           OPTIONAL        1.0             1.0.23          OK         -
 xsane                xsane - Graphical scanner frontend for SANE                  OPTIONAL        0.9             0.998           OK         -
 cups                 CUPS - Common Unix Printing System                           REQUIRED        1.1             1.7.2           OK         'CUPS Scheduler is running'
 policykit            PolicyKit - Administrative policy framework                  OPTIONAL        -               0.105           OK         -
 network              network -wget                                                OPTIONAL        -               1.15            OK         -
 avahi-utils          avahi-utils                                                  OPTIONAL        -               0.6.31          OK         -
 dbus                 DBus - Message bus system                                    REQUIRED        -               1.6.18          OK         -

-------------------------
|  General Dependencies |
-------------------------

 libcrypto            libcrypto - OpenSSL cryptographic library                    REQUIRED        -               1.0.1           OK         -
 python-dbus          Python DBus - Python bindings for DBus                       REQUIRED        0.80.0          1.2.0           OK         -
 reportlab            Reportlab - PDF library for Python                           OPTIONAL        2.0             3.0             OK         -
 python-notify        Python libnotify - Python bindings for the libnotify Desktop notifications OPTIONAL        -               -               OK         -
 pyqt4                PyQt 4- Qt interface for Python (for Qt version 4.x)         REQUIRED        4.0             4.10.4          OK         -
 python-xml           Python XML libraries                                         REQUIRED        -               2.1.0           OK         -
 libusb               libusb - USB library                                         REQUIRED        -               1.0             OK         -
 cups-image           CUPS image - CUPS image development files                    REQUIRED        -               1.7.2           OK         -
 libnetsnmp-devel     libnetsnmp-devel - SNMP networking library development files REQUIRED        5.0.9           5.7.2           OK         -
 sane-devel           SANE - Scanning library development files                    REQUIRED        -               1.0.23          OK         -
 pil                  PIL - Python Imaging Library (required for commandline scanning with hp-scan) OPTIONAL        -               1.1.7           OK         -
 python2X             Python 2.2 or greater - Python programming language          REQUIRED        2.2             2.7.6           OK         -
 pyqt4-dbus           PyQt 4 DBus - DBus Support for PyQt4                         REQUIRED        4.0             4.10.4          OK         -
 libjpeg              libjpeg - JPEG library                                       REQUIRED        -               -               OK         -
 libpthread           libpthread - POSIX threads library                           REQUIRED        -               2.19            OK         -
 python-devel         Python devel - Python development files                      REQUIRED        2.2             2.7.6           OK         -
 cups-devel           CUPS devel- Common Unix Printing System development files    REQUIRED        -               1.7.2           OK         -
 sane                 SANE - Scanning library                                      REQUIRED        -               1.0.23          OK         -

---------------
|  COMPILEDEP |
---------------

 libtool              libtool - Library building support services                  REQUIRED        -               2.4.2           OK         -
 gcc                  gcc - GNU Project C and C++ Compiler                         REQUIRED        -               4.8.4           OK         -
 make                 make - GNU make utility to maintain groups of programs       REQUIRED        3.0             3.81            OK         -

----------------------
|  Python Extentions |
----------------------

 cupsext              CUPS-Extension                                               REQUIRED        -               3.15.7          OK         -
 hpmudext             IO-Extension                                                 REQUIRED        -               3.15.7          OK         -

-----------------------
|  Scan Configuration |
-----------------------

 scanext              Scan-SANE-Extension                                          REQUIRED        -               3.15.7          OK         -
 hpaio                HPLIP-SANE-Backend                                           REQUIRED        -               3.15.7          OK         'hpaio found in /etc/sane.d/dll.conf'

-----------------------
|  Other Dependencies |
-----------------------


------------------------------
| DISCOVERED SCANNER DEVICES |
------------------------------

device `hpaio:/usb/Photosmart_5520_series?serial=CN346140J00602' is a Hewlett-Packard Photosmart_5520_series all-in-one 


--------------------------
| DISCOVERED USB DEVICES |
--------------------------

  Device URI                                            Model                                 
  ----------------------------------------------------  --------------------------------------
  hp:/usb/Photosmart_5520_series?serial=CN346140J00602  HP Photosmart 5520 series             

---------------------------------
| INSTALLED CUPS PRINTER QUEUES |
---------------------------------


[01mPhotosmart_5520[0m
[01m---------------[0m
Type: Printer
Device URI: hp:/usb/Photosmart_5520_series?serial=CN346140J00602
PPD: /etc/cups/ppd/Photosmart_5520.ppd
PPD Description: HP Photosmart 5520 Series, hpcups 3.15.7
Printer status: printer Photosmart_5520 is idle.  enabled since Mon 03 Aug 2015 20:50:25 BST 
Communication status: Good


--------------
| PERMISSION |
--------------

USB             Photosmart_5520                Required        -        -        OK       Node:'/dev/bus/usb/001/003' Perm:'  root  scanner rw- rw- rw- ---'
No errors or warnings


```

---

