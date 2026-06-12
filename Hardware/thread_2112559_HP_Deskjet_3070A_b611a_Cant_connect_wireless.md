---
title: "HP Deskjet 3070A b611a Cant connect wireless"
date: 2013-02-05
forum: Hardware
---

### Post by 0N3 on 2013-02-05
hp-check output is

david@Ubuntu-PC:~$ hp-check

HP Linux Imaging and Printing System (ver. 3.12.11)
Dependency/Version Check Utility ver. 15

Copyright (c) 2001-14 Hewlett-Packard Development Company, LP
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

Saving output in log file: /home/david/hp-check.log

Initializing. Please wait...
warning: ubuntu-13.04 version is not supported. Using ubuntu-12.10 versions dependencies to verify and install...

---------------
| SYSTEM INFO |
---------------

 Kernel: 3.8.0-4-generic #8-Ubuntu SMP Fri Feb 1 18:02:56 UTC 2013 GNU/Linux
 Host: Ubuntu-PC
 Proc: 3.8.0-4-generic #8-Ubuntu SMP Fri Feb 1 18:02:56 UTC 2013 GNU/Linux
 Distribution: ubuntu 13.04

-----------------------
| HPLIP CONFIGURATION |
-----------------------

HPLIP-Version: HPLIP 3.12.11
HPLIP-Home: /usr/share/hplip
warning: HPLIP-Installation: Auto installation is not supported for ubuntu distro  13.04 version 

Current contents of '/etc/hp/hplip.conf' file:
# hplip.conf.  Generated from hplip.conf.in by configure.

[hplip]
version=3.12.11

[dirs]
home=/usr/share/hplip
run=/var/run
ppd=/usr/share/ppd/HP
ppdbase=/usr/share/ppd
doc=/usr/share/doc/hplip-3.12.11
icon=/usr/share/applications
cupsbackend=/usr/lib/cups/backend
cupsfilter=/usr/lib/cups/filter
drv=/usr/share/cups/drv/hp

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
internal-tag=3.12.11
restricted-build=no
ui-toolkit=qt4
qt3=no
qt4=yes
policy-kit=no
hpijs-only-build=no
lite-build=no
udev-acl-rules=yes
udev_sysfs_rules=no
hpcups-only-build=no
hpijs-only-build=no


Current contents of '/var/lib/hp/hplip.state' file:
Plugins are not installed. Could not access file: No such file or directory

Current contents of '~/.hplip/hplip.conf' file:
[upgrade]
notify_upgrade = true
last_upgraded_time = 1360054698
pending_upgrade_time = 0
latest_available_version = 3.12.11

[installation]
date_time = 05/02/13 09:34:55
version = 3.12.11

[settings]
systray_visible = 2
systray_messages = 0

[last_used]
device_uri = 
printer_name = 
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


 <Package-name>        <Package-Desc>      <Required/Optional> <Min-Version> <Installed-Version> <Status>   <Comment>

--------------------------
|  External Dependencies |
--------------------------

 gs                   Ghostscript               REQUIRED        7.05            9.06            OK         -
 network              Network-wget              OPTIONAL        -               1.14            OK         -
 dbus                 DBus                      REQUIRED        -               1.6.8           OK         -
 scanimage            Shell-Scanning            OPTIONAL        1.0             1.0.23          OK         -
 policykit            Admin-Policy-framework    OPTIONAL        -               0.105           OK         -
 xsane                SANE-GUI                  OPTIONAL        0.9             0.998           OK         -
 cups                 CUPS                      REQUIRED        1.1             1.6.1           OK         'CUPS Scheduler is running'

-------------------------
|  General Dependencies |
-------------------------

 reportlab            Python-PDF-Lib            OPTIONAL        2.0             2.5             OK         -
 libcrypto            OpenSSL-Crypto-Lib        REQUIRED        -               1.0.1           OK         -
 pil                  Python-Image-Lib          OPTIONAL        -               1.1.7           OK         -
 pyqt4-dbus           PyQt4-DBUS                REQUIRED        4.0             4.9.6           OK         -
 libjpeg              JPEG-Lib                  REQUIRED        -               -               OK         -
 libpthread           POSIX-Threads-Lib         REQUIRED        -               2.17            OK         -
 python-dbus          Python-DBUS               REQUIRED        0.80.0          1.1.1           OK         -
 python-devel         Python-SDK                REQUIRED        2.2             2.7.3           OK         -
 pyqt4                Python-Qt4                REQUIRED        4.0             4.9.6           OK         -
 cups-devel           CUPS-SDK                  REQUIRED        -               1.6.1           OK         -
 sane-devel           SANE-SDK                  REQUIRED        -               1.0.23          OK         -
 libusb               USB-Lib                   REQUIRED        -               1.0             OK         -
 sane                 Scan-Lib                  REQUIRED        -               1.0.23          OK         -
 cups-image           CUPS-Image-Lib            REQUIRED        -               1.6.1           OK         -
 libnetsnmp-devel     SNMP-Networking-SDK       REQUIRED        5.0.9           5.4.3           OK         -
 python-xml           Python-XML-Lib            REQUIRED        -               2.1.0           OK         -
 python-notify        Desktop-notifications     OPTIONAL        -               -               OK         -

------------------------------
|  Compile Time Dependencies |
------------------------------

 gcc                  gcc-Compiler              REQUIRED        -               4.7.2           OK         -
 libtool              Build-tools               REQUIRED        -               2.4.2           OK         -
 make                 GNU-Build-tools           REQUIRED        3.0             3.81            OK         -

----------------------
|  Python Extentions |
----------------------

 cupsext              CUPS-Extension            REQUIRED        -               3.12.11         OK         -
 pcardext             PhotoCard-Extension       REQUIRED        -               3.12.11         OK         -
 hpmudext             IO-Extension              REQUIRED        -               3.12.11         OK         -

-----------------------
|  Scan Configuration |
-----------------------

 hpaio                HPLIP-SANE-Backend        REQUIRED        -               3.12.11         OK         'hpaio found in /etc/sane.d/dll.conf'
 scanext              Scan-SANE-Extension       REQUIRED        -               3.12.11         OK         -

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

 
Deskjet_3070_B611
-----------------
Type: Printer
Device URI: hp:/usb/Deskjet_3070_B611_series?serial=CN1AA475ZS05MQ
PPD: /etc/cups/ppd/Deskjet_3070_B611.ppd
PPD Description: HP Deskjet 3070 b611 Series, hpcups 3.12.11
Printer status: printer Deskjet_3070_B611 disabled since Tue 05 Feb 2013 09:27:02 GMT - Unplugged or turned off
error: Unable to communicate with device (code=12): hp:/usb/Deskjet_3070_B611_series?serial=CN1AA475ZS05MQ
error: Device not found
error: Communication status: Failed


--------------
| PERMISSION |
--------------

groups          user-groups                    Required        -        -        OK       david adm lp cdrom sudo dip plugdev lpadmin sambashare

 
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

Ubuntu 13.04 64Bit

Says printer is turned off or unplugged when it's clearly on. Installed HP-LIP with no issues entered in my wireless router password ect..... NO ERRORS! Setup completed successfully.

---

