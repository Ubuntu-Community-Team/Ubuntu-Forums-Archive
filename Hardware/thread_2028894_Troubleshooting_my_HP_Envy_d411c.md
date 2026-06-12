---
title: "Troubleshooting my HP Envy d411c"
date: 2012-07-19
forum: Hardware
---

### Post by UltimateCat on 2012-07-19
:)Hi
I installed the hplip-3.12.6 and the printer worked fine yesterday.  Upon turning it on today it shows me the print job but it does not print.
I checked in System>Admin>Printing and have a confirmed "connected to local host"

I ran
```
hp-check -t

```
And wrote down this error message that the terminal gave-
" Unable to communicate with device (code=12) : hp/netENVY_110_series?ip=198.xxx.x.x
```
cat@ztcat:~$ hp-check -t

HP Linux Imaging and Printing System (ver. 3.12.6)
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

Saving output in log file: /home/cat/hp-check.log

Initializing. Please wait...
 
---------------
| SYSTEM INFO |
---------------

 Kernel: 2.6.32-38-generic #83-Ubuntu SMP Wed Jan 4 11:13:04 UTC 2012 GNU/Linux
 Host: ztcat
 Proc: 2.6.32-38-generic #83-Ubuntu SMP Wed Jan 4 11:13:04 UTC 2012 GNU/Linux
 Distribution: ubuntu 10.04

-----------------------
| HPLIP CONFIGURATION |
-----------------------

HPLIP-Version: HPLIP 3.12.6
HPLIP-Home: /usr/share/hplip
HPLIP-Installation: Auto installation is supported for ubuntu distro  10.04 version 

Current contents of '/etc/hp/hplip.conf' file:
# hplip.conf.  Generated from hplip.conf.in by configure.

[hplip]
version=3.12.6

[dirs]
home=/usr/share/hplip
run=/var/run
ppd=/usr/share/ppd/HP
ppdbase=/usr/share/ppd
doc=/usr/share/doc/hplip-3.12.6
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
internal-tag=3.12.6
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
[last_used]
printer_name = 
working_dir = .
device_uri = "hp:/net/ENVY_110_series?ip=192.168.1.8"

[commands]
scan = /usr/bin/xsane -V %SANE_URI%

[upgrade]
notify_upgrade = false
last_upgraded_time = 1342675995.96011
pending_upgrade_time = 0

[installation]
version = 3.12.6
date_time = 07/19/2012 02:23:17

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


 <Package-name>        <Package-Desc>      <Required/Optional> <Min-Version> <Installed-Version> <Status>   <Comment>

--------------------------
|  External Dependencies |
--------------------------

 gs                   Ghostscript               REQUIRED        7.05            8.71            OK         -
 network              Network-wget              OPTIONAL        -               1.12            OK         -
 dbus                 DBus                      REQUIRED        -               1.2.16          OK         -
 scanimage            Shell-Scanning            OPTIONAL        1.0             1.0.20          OK         -
 policykit            Admin-Policy-framework    OPTIONAL        -               0.96            OK         -
 xsane                SANE-GUI                  OPTIONAL        0.9             0.996           OK         -
 cups                 CUPS                      REQUIRED        1.1             1.4.3           OK         'CUPS Scheduler is running'

-------------------------
|  General Dependencies |
-------------------------

 reportlab            Python-PDF-Lib            OPTIONAL        2.0             2.4             OK         -
 libcrypto            OpenSSL-Crypto-Lib        REQUIRED        -               0.9.8           OK         -
 pil                  Python-Image-Lib          OPTIONAL        -               1.1.7           OK         -
 pyqt4-dbus           PyQt4-DBUS                REQUIRED        4.0             4.7.2           OK         -
 libjpeg              JPEG-Lib                  REQUIRED        -               -               OK         -
 libpthread           POSIX-Threads-Lib         REQUIRED        -               2.11.1          OK         -
 python-dbus          Python-DBUS               REQUIRED        0.80.0          0.83.0          OK         -
 python-devel         Python-SDK                REQUIRED        2.2             2.6.5           OK         -
 pyqt4                Python-Qt4                REQUIRED        4.0             4.7.2           OK         -
 cups-devel           CUPS-SDK                  REQUIRED        -               1.4.3           OK         -
 sane-devel           SANE-SDK                  REQUIRED        -               1.0.20          OK         -
 libusb               USB-Lib                   REQUIRED        -               1.0             OK         -
 sane                 Scan-Lib                  REQUIRED        -               1.0.20          OK         -
 cups-image           CUPS-Image-Lib            REQUIRED        -               1.4.3           OK         -
 libnetsnmp-devel     SNMP-Networking-SDK       REQUIRED        5.0.9           5.4.2           OK         -
 python-xml           Python-XML-Lib            REQUIRED        -               2.0.0           OK         -
 python-notify        Desktop-notifications     OPTIONAL        -               -               OK         -

------------------------------
|  Compile Time Dependencies |
------------------------------

 gcc                  gcc-Compiler              REQUIRED        -               4.4.3           OK         -
 libtool              Build-tools               REQUIRED        -               2.2.6           OK         -
 make                 GNU-Build-tools           REQUIRED        3.0             3.81            OK         -

----------------------
|  Python Extentions |
----------------------

 cupsext              CUPS-Extension            REQUIRED        -               3.12.6          OK         -
 pcardext             PhotoCard-Extension       REQUIRED        -               3.12.6          OK         -
 hpmudext             IO-Extension              REQUIRED        -               3.12.6          OK         -

-----------------------
|  Scan Configuration |
-----------------------

 hpaio                HPLIP-SANE-Backend        REQUIRED        -               3.12.6          OK         'hpaio found in /etc/sane.d/dll.conf'
 scanext              Scan-SANE-Extension       REQUIRED        -               3.12.6          OK         -

------------------------------
| DISCOVERED SCANNER DEVICES |
------------------------------

device `hpaio:/net/ENVY_110_series?ip=192.168.1.8' is a Hewlett-Packard ENVY_110_series all-in-one


--------------------------
| DISCOVERED USB DEVICES |
--------------------------

No devices found.

---------------------------------
| INSTALLED CUPS PRINTER QUEUES |
---------------------------------

 
ENVY_110
--------
Type: Printer
Device URI: hp:/net/ENVY_110_series?ip=192.168.1.8
PPD: /etc/cups/ppd/ENVY_110.ppd
PPD Description: HP Envy 110 Series, hpcups 3.12.6
Printer status: printer ENVY_110 is idle.  enabled since Sat 14 Jul 2012 11:56:08 PM EDT
error: Unable to communicate with device (code=12): hp:/net/ENVY_110_series?ip=192.168.1.8
error: unable to open channel
error: Communication status: Failed


--------------
| PERMISSION |
--------------

groups          user-groups                    Required        -        -        OK       cat adm lp dialout fax cdrom audio dip video plugdev fuse lpadmin netdev admin

 
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


```
I have read page after page in Google searches for a fix for " Device communication error 5012"
I shut down and rebooted both computer and printer.  It still fails to print.
The printer worked fine yesterday-
I have not updated my kernel.
The printer connection has been confirmed. 
I have read and tried:
[http://www.pclinuxos.com/forum/index.php?topic=85771.0](http://www.pclinuxos.com/forum/index.php?topic=85771.0)
[http://ubuntuforums.org/showthread.php?t=1249019](http://ubuntuforums.org/showthread.php?t=1249019)
I could post all of the websites I've been to for help but I think at this point it's not helpful.  I don't get what is going on here; please ( I've already spent 22 hours with this printer) I'm running low on engery and out of ideas?
Could it be that I am missing dependencies?
How would I tell?

---

### Post by UltimateCat on 2012-07-20
I read through very throughly the output from the terminal and determined that I do not have any missing dependencies.

I only have till next week to return this printer.  I really don't want to do that.
HP told me over the telephone that they are not Linux certified but they are working on it.  This is a shame because a lot o folks are coming to Linux-

The HP Icon is on my desktop along with my clock and firewall icon so that's the confirmation that the install went well.

Has anyone else experienced this?
Printer works fine one day and the next...won't even print?-

I've never had this much trouble getting Ubuntu to make a printer comply. I'm really confused at this point :confused:

Please help

---

### Post by UltimateCat on 2012-07-22
Ended up having to un-install the hplip because the printer stopped working.

---

