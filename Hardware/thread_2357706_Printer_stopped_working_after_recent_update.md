---
title: "Printer stopped working after recent update"
date: 2017-04-05
forum: Hardware
---

### Post by wicki on 2017-04-05
Hi First post and a newbie so please be gentle.
After the latest update my HP 3050 scan printer stopped working i was using the drivers that came with Ubuntu 16.04lts, I tried to install hplip but i had a permission problem on the driver file so changed the permissions and the errors disappeared but it still wont print all the docs/jobs appear in the que and says it is complete but nothing happens moved the printer to a windows laptop and all works.

here is the HPLIP diagnostic can any one advise me please what to do....and should i upgrade Ubuntu when it says system updates available or leave sleeping dogs alone?

```
HP Linux Imaging and Printing System (ver. 3.16.11)
Self Diagnse Utility and Healing Utility ver. 1.0


Copyright (c) 2001-15 HP Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.




HP Linux Imaging and Printing System (ver. 3.16.11)
Self Diagnse Utility and Healing Utility ver. 1.0


Copyright (c) 2001-15 HP Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.


 


Checking for Deprecated items....
No Deprecated items are found




Checking for HPLIP updates....


HP Linux Imaging and Printing System (ver. 3.16.11)
HPLIP upgrade latest version ver. 1.0


Copyright (c) 2001-15 HP Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.


Latest version of HPLIP is already installed.




Checking for Dependencies....


---------------
| SYSTEM INFO |
---------------


 Kernel: 4.4.0-72-generic #93-Ubuntu SMP Fri Mar 31 14:07:41 UTC 2017 GNU/Linux
 Host: alec-Dell-XPS420
 Proc: 4.4.0-72-generic #93-Ubuntu SMP Fri Mar 31 14:07:41 UTC 2017 GNU/Linux
 Distribution: 12 16.04
 Bitness: 64 bit




-----------------------
| HPLIP CONFIGURATION |
-----------------------


HPLIP-Version: HPLIP 3.16.11
HPLIP-Home: /usr/share/hplip
HPLIP-Installation: Auto installation is supported for ubuntu distro  16.04 version 


Current contents of '/etc/hp/hplip.conf' file:
# hplip.conf.  Generated from hplip.conf.in by configure.


[hplip]
version=3.16.11


[dirs]
home=/usr/share/hplip
run=/var/run
ppd=/usr/share/ppd/HP
ppdbase=/usr/share/ppd
doc=/usr/share/doc/hplip-3.16.11
html=/usr/share/doc/hplip-3.16.11
icon=/usr/share/applications
cupsbackend=/usr/lib/cups/backend
cupsfilter=/usr/lib/cups/filter
drv=/usr/share/cups/drv/hp
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
hpijs-install=no
foomatic-drv-install=no
foomatic-ppd-install=no
foomatic-rip-hplip-install=no
hpcups-install=yes
cups-drv-install=yes
cups-ppd-install=no
internal-tag=3.16.11
restricted-build=no
ui-toolkit=qt4
qt3=no
qt4=yes
qt5=no
policy-kit=no
lite-build=no
udev_sysfs_rules=no
hpcups-only-build=no
hpijs-only-build=no
apparmor_build=yes




Current contents of '/var/lib/hp/hplip.state' file:
Plugins are not installed. Could not access file: No such file or directory


Current contents of '~/.hplip/hplip.conf' file:
[upgrade]
notify_upgrade = true
last_upgraded_time = 1491301868
pending_upgrade_time = 0
latest_available_version = 3.16.11


[settings]
systray_visible = 0
systray_messages = 0


[last_used]
device_uri = "hp:/usb/Deskjet_3050_J610_series?serial=CN1133D2BG05HX"
printer_name = Deskjet_3050_J610
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
date_time = 05/04/2017 10:33:27
version = 3.16.11




 <Package-name>        <Package-Desc>      <Required/Optional> <Min-Version> <Installed-Version> <Status>   <Comment>


--------------
| COMPILEDEP |
--------------


 gcc                  gcc - GNU Project C and C++ Compiler                         REQUIRED        -               5.4.0           OK         -
 make                 make - GNU make utility to maintain groups of programs       REQUIRED        3.0             4.1             OK         -
 libtool              libtool - Library building support services                  REQUIRED        -               2.4.6           OK         -


------------------------
| General Dependencies |
------------------------


 libcrypto            libcrypto - OpenSSL cryptographic library                    REQUIRED        -               1.0.2           OK         -
 python-xml           Python XML libraries                                         REQUIRED        -               2.1.0           OK         -
 libnetsnmp-devel     libnetsnmp-devel - SNMP networking library development files REQUIRED        5.0.9           5.7.3           OK         -
 sane-devel           SANE - Scanning library development files                    REQUIRED        -               1.0.25          OK         -
 pil                  PIL - Python Imaging Library (required for commandline scanning with hp-scan) OPTIONAL        -               1.1.7           OK         -
 pyqt4-dbus           PyQt 4 DBus - DBus Support for PyQt4                         REQUIRED        4.0             4.11.4          OK         -
 libpthread           libpthread - POSIX threads library                           REQUIRED        -               2.23            OK         -
 python-devel         Python devel - Python development files                      REQUIRED        2.2             2.7.12          OK         -
 cups-devel           CUPS devel- Common Unix Printing System development files    REQUIRED        -               2.1.3           OK         -
 python-dbus          Python DBus - Python bindings for DBus                       REQUIRED        0.80.0          1.2.0           OK         -
 cups-ddk             CUPS DDK - CUPS driver development kit                       OPTIONAL        -               -               OK         -
 reportlab            Reportlab - PDF library for Python                           OPTIONAL        2.0             3.3.0           OK         -
 pyqt4                PyQt 4- Qt interface for Python (for Qt version 4.x)         REQUIRED        4.0             4.11.4          OK         -
 libusb               libusb - USB library                                         REQUIRED        -               1.0             OK         -
 cups-image           CUPS image - CUPS image development files                    REQUIRED        -               2.1.3           OK         -
 python2X             Python 2.2 or greater - Python programming language          REQUIRED        2.2             2.7.12          OK         -
 python-notify        Python libnotify - Python bindings for the libnotify Desktop notifications OPTIONAL        -               -               OK         -
 libjpeg              libjpeg - JPEG library                                       REQUIRED        -               -               OK         -
 sane                 SANE - Scanning library                                      REQUIRED        -               1.0.25          OK         -


----------------------
| Scan Configuration |
----------------------


 scanext              Scan-SANE-Extension                                          REQUIRED        -               3.16.11         OK         -
 hpaio                HPLIP-SANE-Backend                                           REQUIRED        -               3.16.11         OK         'hpaio found in /etc/sane.d/dll.conf'


-------------------------
| External Dependencies |
-------------------------


 gs                   GhostScript - PostScript and PDF language interpreter and previewer REQUIRED        7.05            9.18            OK         -
 cups                 CUPS - Common Unix Printing System                           REQUIRED        1.1             2.1.3           OK         'CUPS Scheduler is running'
 network              network -wget                                                OPTIONAL        -               1.17.1          OK         -
 scanimage            scanimage - Shell scanning program                           OPTIONAL        1.0             1.0.25          OK         -
 policykit            PolicyKit - Administrative policy framework                  OPTIONAL        -               0.105           OK         -
 xsane                xsane - Graphical scanner frontend for SANE                  OPTIONAL        0.9             0.999           OK         -
 dbus                 DBus - Message bus system                                    REQUIRED        -               1.10.6          OK         -
 avahi-utils          avahi-utils                                                  OPTIONAL        -               0.6.32          OK         -


---------------------
| Python Extentions |
---------------------


 hpmudext             IO-Extension                                                 REQUIRED        -               3.16.11         OK         -
 cupsext              CUPS-Extension                                               REQUIRED        -               3.16.11         OK         -


------------------------------
| DISCOVERED SCANNER DEVICES |
------------------------------


device `hpaio:/usb/Deskjet_3050_J610_series?serial=CN1133D2BG05HX' is a Hewlett-Packard Deskjet_3050_J610_series all-in-one




--------------------------
| DISCOVERED USB DEVICES |
--------------------------


  Device URI                        Model                      
  --------------------------------  ---------------------------
  hp:/usb/Deskjet_3050_J610_series  HP Deskjet 3050 J610 series
  ?serial=CN1133D2BG05HX                                       


---------------------------------
| INSTALLED CUPS PRINTER QUEUES |
---------------------------------


 
Deskjet_3050_J610
-----------------
Type: Printer
Device URI: hp:/usb/Deskjet_3050_J610_series?serial=CN1133D2BG05HX
PPD: /etc/cups/ppd/Deskjet_3050_J610.ppd
PPD Description: HP LaserJet 3050 Postscript (recommended)
Printer status: printer Deskjet_3050_J610 is idle.  enabled since mer. 05 avril 2017 10:ready to print
Communication status: Good




--------------
| PERMISSION |
--------------


USB             Deskjet_3050_J610              Required        -        -        OK       Node:'/dev/bus/usb/002/003' Perm:'  root  lp rw- rw- rw- rw- r--'
 


Checking for Configured Queues....
 
Queue(s) configured correctly using HPLIP.




Checking for HP Properitery Plugin's....
No plug-in printers are configured.
 
Diagnose completed...






More information on Troubleshooting,How-To's and Support is available on [http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html)




Please close this terminal manually.
```

---

### Post by slickymaster on 2017-04-05
*Thread moved to **Hardware**.*

---

### Post by howefield on 2017-04-05
I'd suggest the easy stuff first if you haven't already done it and that would be to delete the printer from System Settings > Printers and then reinstall it.

I had a similar issue with a different printer model but successfully installed it via the web browser @ localhost:631 might be worth trying with no harm done.

---

### Post by pdc on 2017-04-05
Hi wiki

when you say ```
After the latest update my HP 3050 scan printer stopped working
```, it sounds awfully like this [https://forums.linuxmint.com/viewtopic.php?f=51&t=242497](https://forums.linuxmint.com/viewtopic.php?f=51&t=242497)

where the update of 2.1.3-4ubuntu0.2 caused issues; if you COPY this command and paste it into a terminal; and then copy the result; and paste it back here: please ask if you need a how-to for all that; ```
dpkg -l cups*
```

_______

thanks for the first diagnostic: which command did you run?

HP also suggest ```
hp-check -t
```        [http://hplipopensource.com/node/332#printing2](http://hplipopensource.com/node/332#printing2)        can you also run that? ..... if that was what we already got, great!

---

### Post by wicki on 2017-04-06
The Diagnostic is the in built with HPLIP .

I have now solved this problem as my install was quite new and printing a critical requirement for my biz i did a quick reinstall and all is good with only the apps included in Ubuntu.

---

### Post by wicki on 2017-06-01
So it has happen'd again printer has stopped to function for no apparent reason.

there is a message saying there is a missing print filter .....any one have an idea what to do?

---

### Post by sulatha on 2017-06-07
> **howefield said:**
> I'd suggest the easy stuff first if you haven't already done it and that would be to delete the printer from System Settings > Printers and then reinstall it.

I had a similar issue with a different printer model but successfully installed [[COLOR=#000000]HP LaserJet P1006 Driver[/COLOR]]("https://www.drivers-hp.com/hp-laserjet-p1006-driver/") it via the web browser @ localhost:631 might be worth trying with no harm done.

thanks for the solution the above method solved my issue

---

