---
title: "Accessing HP Laserjet M1132P printer from Windows computer over SMB"
date: 2015-01-28
forum: Hardware
---

### Post by seljer on 2015-01-28
Hello all. I have a bit of trouble acessing a printer -> hp Laserjet M1132P MFD -> which is shared from a computer running Windows 7. I myself am running Xubuntu 14.04.

I can see it on the network and add it to the list of printers in the GUI printer control panel (manually selecting the driver) but theres some kind of driver issue preventing me from actually using it. 

Heres the output of "hp_check -t"
[FONT=courier new]
HP Linux Imaging and Printing System (ver. 3.14.3)
Dependency/Version Check Utility ver. 15.1

Copyright (c) 2001-13 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

Note: hp-check can be run in three modes:
1. Compile-time check mode (-c or --compile): Use this mode before compiling the HPLIP supplied tarball (.tar.gz or .run) to determine if the proper dependencies are installed to successfully      
compile HPLIP.                                                                                                                                                                                       
2. Run-time check mode (-r or --run): Use this mode to determine if a distro supplied package (.deb, .rpm, etc) or an already built HPLIP supplied tarball has the proper dependencies installed to  
successfully run.                                                                                                                                                                                    
3. Both compile- and run-time check mode (-b or --both) (Default): This mode will check both of the above cases (both compile- and run-time dependencies).                                           

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

warning: ubuntu-14.04 version is not supported. Using ubuntu-13.10 versions dependencies to verify and install...

---------------
| SYSTEM INFO |
---------------

 Kernel: 3.13.0-40-generic #69-Ubuntu SMP Thu Nov 13 17:56:26 UTC 2014 GNU/Linux
 Host: ThinkPad
 Proc: 3.13.0-40-generic #69-Ubuntu SMP Thu Nov 13 17:56:26 UTC 2014 GNU/Linux
 Distribution: ubuntu 14.04
 Bitness: 32 bit


-----------------------
| HPLIP CONFIGURATION |
-----------------------

HPLIP-Version: HPLIP 3.14.3
HPLIP-Home: /usr/share/hplip
warning: HPLIP-Installation: Auto installation is not supported for ubuntu distro  14.04 version 

Current contents of '/etc/hp/hplip.conf' file:
# hplip.conf.  Generated from hplip.conf.in by configure.

[hplip]
version=3.14.3

[dirs]
home=/usr/share/hplip
run=/var/run
ppd=/usr/share/ppd/hplip/HP
ppdbase=/usr/share/ppd/hplip
doc=/usr/share/doc/hplip-doc/HTML
html=/usr/share/doc/hplip-3.14.3
icon=no
cupsbackend=/usr/lib/cups/backend
cupsfilter=/usr/lib/cups/filter
drv=/usr/share/cups/drv
bin=/usr/bin

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
internal-tag=3.14.3
restricted-build=no
ui-toolkit=qt4
qt3=no
qt4=yes
policy-kit=yes
lite-build=no
udev_sysfs_rules=no
hpcups-only-build=no
hpijs-only-build=no


Current contents of '/var/lib/hp/hplip.state' file:
[plugin]
installed = 1
eula = 1
version = 3.14.3



Current contents of '~/.hplip/hplip.conf' file:
[upgrade]
latest_available_version = 3.12.10a

[installation]
date_time = 01/28/2015 17:50:59
version = 3.14.3


 <Package-name>        <Package-Desc>      <Required/Optional> <Min-Version> <Installed-Version> <Status>   <Comment>

--------------------------
|  External Dependencies |
--------------------------

 policykit            Admin-Policy-framework    OPTIONAL        -               0.105           OK         -
 gs                   Ghostscript               REQUIRED        7.05            9.10            OK         -
 network              Network-wget              OPTIONAL        -               1.15            OK         -
 scanimage            Shell-Scanning            OPTIONAL        1.0             1.0.23          OK         -
 avahi-utils          avahi-utils               OPTIONAL        -               0.6.31          OK         -
 error: dbus          DBus                      REQUIRED        -               1.6.18          MISSING    'DBUS may not be installed or not running'
 error: cups          CUPS                      REQUIRED        1.1             -               INCOMPAT   'CUPS may not be installed or not running'
 error: xsane         SANE-GUI                  OPTIONAL        0.9             -               MISSING    'xsane needs to be installed'

-------------------------
|  General Dependencies |
-------------------------

 reportlab            Python-PDF-Lib            OPTIONAL        2.0             3.0             OK         -
 error: libcrypto     OpenSSL-Crypto-Lib        REQUIRED        -               1.0.1           MISSING    'libcrypto needs to be installed'
 pil                  Python-Image-Lib          OPTIONAL        -               1.1.7           OK         -
 pyqt4-dbus           PyQt4-DBUS                REQUIRED        4.0             4.10.4          OK         -
 error: libjpeg       JPEG-Lib                  REQUIRED        -               -               MISSING    'libjpeg needs to be installed'
 error: libpthread    POSIX-Threads-Lib         REQUIRED        -               2.19            MISSING    'libpthread needs to be installed'
 python-dbus          Python-DBUS               REQUIRED        0.80.0          1.2.0           OK         -
 error: python-devel  Python-SDK                REQUIRED        2.2             2.7.6           MISSING    'python-devel needs to be installed'
 pyqt4                Python-Qt4                REQUIRED        4.0             4.10.4          OK         -
 error: cups-devel    CUPS-SDK                  REQUIRED        -               -               MISSING    'cups-devel needs to be installed'
 error: sane-devel    SANE-SDK                  REQUIRED        -               -               MISSING    'sane-devel needs to be installed'
 libusb               USB-Lib                   REQUIRED        -               1.0             OK         -
 sane                 Scan-Lib                  REQUIRED        -               -               OK         -
 error: cups-image    CUPS-Image-Lib            REQUIRED        -               -               MISSING    'cups-image needs to be installed'
 error: libnetsnmp-devel SNMP-Networking-SDK       REQUIRED        5.0.9           -               MISSING    'libnetsnmp-devel needs to be installed'
 python-xml           Python-XML-Lib            REQUIRED        -               2.1.0           OK         -
 python-notify        Desktop-notifications     OPTIONAL        -               -               OK         -

------------------------------
|  Compile Time Dependencies |
------------------------------

 error: gcc           gcc-Compiler              REQUIRED        -               4.8.2           MISSING    'gcc needs to be installed'
 error: libtool       Build-tools               REQUIRED        -               -               MISSING    'libtool needs to be installed'
 make                 GNU-Build-tools           REQUIRED        3.0             3.81            OK         -

----------------------
|  Python Extentions |
----------------------

 cupsext              CUPS-Extension            REQUIRED        -               3.14.3          OK         -
 pcardext             PhotoCard-Extension       REQUIRED        -               3.14.3          OK         -
 hpmudext             IO-Extension              REQUIRED        -               3.14.3          OK         -

-----------------------
|  Scan Configuration |
-----------------------

 hpaio                HPLIP-SANE-Backend        REQUIRED        -               3.14.3          OK         'hpaio found in /etc/sane.d/dll.conf'
 scanext              Scan-SANE-Extension       REQUIRED        -               3.14.3          OK         -

------------------------------
| DISCOVERED SCANNER DEVICES |
------------------------------

No Scanner found.

--------------------------
| DISCOVERED USB DEVICES |
--------------------------

No devices found.

---------------------------------
| INSTALLED CUPS PRINTER QUEUES |
---------------------------------

 
Hewlett-Packard-HP-LaserJet-1018
--------------------------------
Type: Printer
Device URI: hp:/usb/HP_LaserJet_1018?serial=KP1C8YK
PPD: /etc/cups/ppd/Hewlett-Packard-HP-LaserJet-1018.ppd
PPD Description: HP LaserJet 1018 Foomatic/foo2zjs-z1 (recommended)
Printer status: printer Hewlett-Packard-HP-LaserJet-1018 is idle.  enabled since Mon 19 Jan 2015 12:26:12 PM CET
Required plug-in status: Installed
error: Unable to communicate with device (code=12): hp:/usb/HP_LaserJet_1018?serial=KP1C8YK
error: Device not found
error: Communication status: Failed
[B]
HP-LaserJet-Professional-m1132-MFP
----------------------------------
Type: Unknown
Device URI: smb://WORKGROUP/WIN-PC/HP%20LaserJet%20Professional%20M1132%20MFP
PPD: /etc/cups/ppd/HP-LaserJet-Professional-m1132-MFP.ppd
PPD Description: HP LaserJet Professional m1132 MFP, hpcups 3.14.3, requires proprietary plugin
Printer Rendering completedLaserJet-Professional-m1132-MFP is idle.  enabled since Wed 28 Jan 2015 05:33:19 PM CET
warning: Printer is not HPLIP installed. Printers must use the hp: or hpfax: CUPS backend for HP-Devices.[/B]


--------------
| PERMISSION |
--------------

 
-----------
| SUMMARY |
-----------

Missing Required Dependencies
-----------------------------
error: 'libdbus-1-dev' package is missing/incompatible 
error: 'libcups2' package is missing/incompatible 
error: 'openssl' package is missing/incompatible 
error: 'libjpeg-dev' package is missing/incompatible 
error: 'build-essential' package is missing/incompatible 
error: 'python-dev' package is missing/incompatible 
error: 'libcups2-dev' package is missing/incompatible 
error: 'cups-bsd' package is missing/incompatible 
error: 'cups-client' package is missing/incompatible 
error: 'libsane-dev' package is missing/incompatible 
error: 'libcupsimage2-dev' package is missing/incompatible 
error: 'libsnmp-dev' package is missing/incompatible 
error: 'snmp-mibs-downloader' package is missing/incompatible 
error: 'build-essential' package is missing/incompatible 
error: 'libtool' package is missing/incompatible 

Missing Optional Dependencies
-----------------------------
error: 'gtk2-engines-pixbuf' package is missing/incompatible 
error: 'xsane' package is missing/incompatible 

Total Errors: 14
Total Warnings: 1

Run 'hp-doctor' command to prompt and fix the issues. 

Done.

[/FONT]Ignor the Laserjet 1018, thats a different printer I occasionaly hook up to directly via USB cable and it works fine. It's the networked one I'd like to get working if that is even possible. Anyone have and idea how to approach this?.[FONT=courier new]
[/FONT]

---

