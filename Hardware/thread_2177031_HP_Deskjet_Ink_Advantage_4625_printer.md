---
title: "HP Deskjet Ink Advantage 4625 printer"
date: 2013-09-26
forum: Hardware
---

### Post by Edgar_Sarmento_Bezerra on 2013-09-26
Hi :D
I'm newbie and a Ubuntu 12.04 LTS user.
My ALSA information: [http://www.alsa-project.org/db/?f=ff...748303ae35b0c4]("http://www.alsa-project.org/db/?f=ffa30916bb0b5ca6973c61f798748303ae35b0c4")
Website of the printer: [http://www8.hp.com/br/pt/hp-search/search-results.html?ajaxpage=1#/page=1&/cc=br&/lang=pt&/qt=hp%20deskjet%20ink%20advantage%204625](http://www8.hp.com/br/pt/hp-search/search-results.html?ajaxpage=1#/page=1&/cc=br&/lang=pt&/qt=hp%20deskjet%20ink%20advantage%204625)
Could somebody help me?

---

### Post by coldraven on 2013-09-27
Have you tried just plugging it in?
Open the Printers utility by typing PRINT in the Dash, then wait for a moment to see if it automatically finds it.
If not click on "Add" Printer and wait for a few moments again.
My Epson just appears without me doing anything.
I cannot read your HP link because it is not in English.

---

### Post by Frogs Hair on 2013-09-27
[http://hplipopensource.com/hplip-web/models/deskjet_aio/deskjet_4620_series.html](http://hplipopensource.com/hplip-web/models/deskjet_aio/deskjet_4620_series.html)

---

### Post by Edgar_Sarmento_Bezerra on 2013-09-28
> **coldraven said:**
> Have you tried just plugging it in?
Open the Printers utility by typing PRINT in the Dash, then wait for a moment to see if it automatically finds it.
If not click on "Add" Printer and wait for a few moments again.
My Epson just appears without me doing anything.
I cannot read your HP link because it is not in English.

Oh I'm sorry I haven't realized that. That's the english website: [http://www8.hp.com/us/en/hp-search/search-results.html?ajaxpage=1#/page=1&/cat=Support%20%26%20Drivers&/cc=us&/lang=en&/qt=Deskjet%20Ink%20Advantage%204625](http://www8.hp.com/us/en/hp-search/search-results.html?ajaxpage=1#/page=1&/cat=Support%20%26%20Drivers&/cc=us&/lang=en&/qt=Deskjet%20Ink%20Advantage%204625) 
Well, I'll try to do what you said. :)

---

### Post by Edgar_Sarmento_Bezerra on 2013-09-28
> **Frogs Hair said:**
> [http://hplipopensource.com/hplip-web/models/deskjet_aio/deskjet_4620_series.html](http://hplipopensource.com/hplip-web/models/deskjet_aio/deskjet_4620_series.html)

Thanks, man. I'll try to solve my problem now. :D

---

### Post by Edgar_Sarmento_Bezerra on 2013-09-28
Frogs Hair*, *I'm printing! :)
I'm really thankful for your help! Thanks for posting the website! My problem is solved! :biggrin:

---

### Post by Edgar_Sarmento_Bezerra on 2013-10-02
I'm with problems. I can't print anymore :(
I try to print and it doesn't work, there just appears a box informing that it's printed but it hasn't.
What should I do?

---

### Post by Edgar_Sarmento_Bezerra on 2013-10-02
When I've selected "Diagnose HPLIP Driver" that's what have appeared in terminal:
"HP Linux Imaging and Printing System (ver. 3.13.9)
Self Diagnse Utility and Healing Utility ver. 1.0

Copyright (c) 2001-13 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

 

Checking for Deprecated items....
No Deprecated items are found


Checking for HPLIP updates....
Latest version of HPLIP is already installed.


Checking for Dependencies....

---------------
| SYSTEM INFO |
---------------

 Kernel: 3.8.0-31-generic #46~precise1-Ubuntu SMP Wed Sep 11 18:21:16 UTC 2013 GNU/Linux
 Host: edgar-RV411-RV511-E3511-S3511-RV711-E3411
 Proc: 3.8.0-31-generic #46~precise1-Ubuntu SMP Wed Sep 11 18:21:16 UTC 2013 GNU/Linux
 Distribution: ubuntu 12.04
 Bitness: 64 bit


-----------------------
| HPLIP CONFIGURATION |
-----------------------

HPLIP-Version: HPLIP 3.13.9
HPLIP-Home: /usr/share/hplip
HPLIP-Installation: Auto installation is supported for ubuntu distro  12.04 version 

Current contents of '/etc/hp/hplip.conf' file:
# hplip.conf.  Generated from hplip.conf.in by configure.

[hplip]
version=3.13.9

[dirs]
home=/usr/share/hplip
run=/var/run
ppd=/usr/share/ppd/HP
ppdbase=/usr/share/ppd
doc=/usr/share/doc/hplip-3.13.9
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
internal-tag=3.13.9
restricted-build=no
ui-toolkit=qt4
qt3=no
qt4=yes
policy-kit=no
lite-build=no
udev-acl-rules=yes
udev_sysfs_rules=no
hpcups-only-build=no
hpijs-only-build=no


Current contents of '/var/lib/hp/hplip.state' file:
# hplip.state - HPLIP runtime persistent variables. 

[plugin]
installed=0
eula=0



Current contents of '~/.hplip/hplip.conf' file:
[installation]
date_time = 10/03/2013 00:04:27
version = 3.13.9

[upgrade]
notify_upgrade = true
last_upgraded_time = 1380418823
pending_upgrade_time = 0
latest_available_version = 3.13.9

[settings]
systray_visible = 0
systray_messages = 0

[last_used]
device_uri = "hp:/net/Deskjet_4620_series?ip=192.168.0.2"
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

 policykit            Admin-Policy-framework    OPTIONAL        -               0.104           OK         -
 gs                   Ghostscript               REQUIRED        7.05            9.05            OK         -
 network              Network-wget              OPTIONAL        -               1.13.4          OK         -
 scanimage            Shell-Scanning            OPTIONAL        1.0             1.0.22          OK         -
 avahi-utils          avahi-utils               OPTIONAL        -               0.6.30          OK         -
 dbus                 DBus                      REQUIRED        -               1.4.18          OK         -
 cups                 CUPS                      REQUIRED        1.1             1.5.3           OK         'CUPS Scheduler is running'
 xsane                SANE-GUI                  OPTIONAL        0.9             0.998           OK         -

-------------------------
|  General Dependencies |
-------------------------

 reportlab            Python-PDF-Lib            OPTIONAL        2.0             2.5             OK         -
 libcrypto            OpenSSL-Crypto-Lib        REQUIRED        -               1.0.1           OK         -
 pil                  Python-Image-Lib          OPTIONAL        -               1.1.7           OK         -
 pyqt4-dbus           PyQt4-DBUS                REQUIRED        4.0             4.9.1           OK         -
 libjpeg              JPEG-Lib                  REQUIRED        -               -               OK         -
 libpthread           POSIX-Threads-Lib         REQUIRED        -               2.15            OK         -
 python-dbus          Python-DBUS               REQUIRED        0.80.0          1.0.0           OK         -
 python-devel         Python-SDK                REQUIRED        2.2             2.7.3           OK         -
 pyqt4                Python-Qt4                REQUIRED        4.0             4.9.1           OK         -
 cups-devel           CUPS-SDK                  REQUIRED        -               1.5.3           OK         -
 sane-devel           SANE-SDK                  REQUIRED        -               1.0.22          OK         -
 libusb               USB-Lib                   REQUIRED        -               1.0             OK         -
 sane                 Scan-Lib                  REQUIRED        -               1.0.22          OK         -
 cups-image           CUPS-Image-Lib            REQUIRED        -               1.5.3           OK         -
 libnetsnmp-devel     SNMP-Networking-SDK       REQUIRED        5.0.9           5.4.3           OK         -
 python-xml           Python-XML-Lib            REQUIRED        -               2.0.1           OK         -
 python-notify        Desktop-notifications     OPTIONAL        -               -               OK         -

------------------------------
|  Compile Time Dependencies |
------------------------------

 gcc                  gcc-Compiler              REQUIRED        -               4.6.3           OK         -
 libtool              Build-tools               REQUIRED        -               2.4.2           OK         -
 make                 GNU-Build-tools           REQUIRED        3.0             3.81            OK         -

----------------------
|  Python Extentions |
----------------------

 cupsext              CUPS-Extension            REQUIRED        -               3.13.9          OK         -
 pcardext             PhotoCard-Extension       REQUIRED        -               3.13.9          OK         -
 hpmudext             IO-Extension              REQUIRED        -               3.13.9          OK         -

-----------------------
|  Scan Configuration |
-----------------------

 hpaio                HPLIP-SANE-Backend        REQUIRED        -               3.13.9          OK         'hpaio found in /etc/sane.d/dll.conf'
 scanext              Scan-SANE-Extension       REQUIRED        -               3.13.9          OK         -

------------------------------
| DISCOVERED SCANNER DEVICES |
------------------------------

device `hpaio:/net/Deskjet_4620_series?ip=192.168.0.2' is a Hewlett-Packard Deskjet_4620_series all-in-one


--------------------------
| DISCOVERED USB DEVICES |
--------------------------

No devices found.

---------------------------------
| INSTALLED CUPS PRINTER QUEUES |
---------------------------------

 
Deskjet_4620
------------
Type: Printer
Device URI: hp:/net/Deskjet_4620_series?ip=192.168.0.2
PPD: /etc/cups/ppd/Deskjet_4620.ppd
PPD Description: HP Deskjet 4620 Series, hpcups 3.13.9
Printer status: printer Deskjet_4620 is idle.  enabled since Thu 03 Oct 2013 12:00:03 AM/usr/lib/cups/backend/hp failed
error: Unable to communicate with device (code=12): hp:/net/Deskjet_4620_series?ip=192.168.0.2
error: unable to open channel
error: Communication status: Failed

Deskjet_4620_fax
----------------
Type: Fax
Device URI: hpfax:/net/Deskjet_4620_series?ip=192.168.0.2
PPD: /etc/cups/ppd/Deskjet_4620_fax.ppd
PPD Description: HP Fax4 hpcups
Printer status: printer Deskjet_4620_fax is idle.  enabled since Sat 28 Sep 2013 10:44:43 PM BRT
error: Unable to communicate with device (code=12): hpfax:/net/Deskjet_4620_series?ip=192.168.0.2
error: unable to open channel
error: Communication status: Failed


--------------
| PERMISSION |
--------------

groups          user-groups                    Required        -        -        OK       edgar adm lp cdrom sudo dip plugdev lpadmin sambashare

 

Checking Permissions....
Permissions are correct.


Checking for Configured Queues....
 
Queue(s) configured correctly using HPLIP.


Checking for HP Properitery Plugin's....
HP Properitery Plugin's are not required as no plug-in printer is present.
 

Checking for Printer Status....
error: 'Deskjet_4620_fax' Printer is either Powered-OFF or Failed to communicate.
Turn On Printer and re-run hp-doctor
error: 'Deskjet_4620' Printer is either Powered-OFF or Failed to communicate.
Turn On Printer and re-run hp-doctor

Diagnose completed...



More information on Troubleshooting,How-To's and Support is available on [http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html)


Please close this terminal manually."

I hope it helps.

---

### Post by Cbjaxx on 2013-10-03
I will assume it is powered on, but did the printer fall off your network? That bottom part where it is checking for a printer status it states:
> Checking for Printer Status....
error: 'Deskjet_4620' Printer is either Powered-OFF or Failed to communicate.
Turn On Printer and re-run hp-doctor

You can try to ping your printer from the terminal ```
ping -c 3 192.168.0.2
``` if you get a reply, then we can assume it is on your network.

---

### Post by Edgar_Sarmento_Bezerra on 2013-10-07
> **Cbjaxx said:**
> I will assume it is powered on, but did the printer fall off your network? That bottom part where it is checking for a printer status it states:


You can try to ping your printer from the terminal ```
ping -c 3 192.168.0.2
``` if you get a reply, then we can assume it is on your network.

Answer from the terminal:
"edgar@edgar-RV411-RV511-E3511-S3511-RV711-E3411:~$ ping -c 3 192.168.0.2
PING 192.168.0.2 (192.168.0.2) 56(84) bytes of data.
From 192.168.0.7 icmp_seq=1 Destination Host Unreachable
From 192.168.0.7 icmp_seq=2 Destination Host Unreachable
From 192.168.0.7 icmp_seq=3 Destination Host Unreachable

--- 192.168.0.2 ping statistics ---
3 packets transmitted, 0 received, +3 errors, 100% packet loss, time 2015ms
pipe 3"

---

### Post by Edgar_Sarmento_Bezerra on 2013-10-09
I don't understand that! 
I've installed again the HPLIP of my printer and it's worked. But as soon as I shut down the pc and come back to use it and try to print something, it simply doesn't work anymore. 
My printer works through wireless. 
Help me, please. :(

---

### Post by flaviocpontes on 2014-02-02
I have an HP Deskjet Ink Advantage 5525.
I used this guide to help me install it: [https://help.ubuntu.com/community/HpAllInOne](https://help.ubuntu.com/community/HpAllInOne)

---

