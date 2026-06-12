---
title: "Unable to make HP Officejet J4660 work"
date: 2018-01-23
forum: Hardware
---

### Post by talestomaz on 2018-01-23
Hi all,

I'm trying to make a HP Officejet J4660 work on my Ubuntu 16.04. It worked previously on my brother's Ubuntu 14.04 and works fine on Windows, so I think it's just something about settings and configuration.

I have already installed HPLIP. Installation seemed to be flawless, except for this: [https://drive.google.com/file/d/1W3gMd8H3TphXXq3FT-zpYHpl9hHMb_4x/view?usp=sharing](https://drive.google.com/file/d/1W3gMd8H3TphXXq3FT-zpYHpl9hHMb_4x/view?usp=sharing). I did eventually choose to install the plugin in spite of not receiving the key from the keyserver.

As installation went on, I assumed it was no huge problem. However, after installation finished and HP Setup tried to find the printer, I saw this screen: [https://drive.google.com/open?id=1tB3HEVqr8BzPKgbRIGAb4UmYEcqTIEy4](https://drive.google.com/open?id=1tB3HEVqr8BzPKgbRIGAb4UmYEcqTIEy4).

After some refresh, it seemed to find the printer, but then another message popped up indicating that the communication problem appeared again: [https://drive.google.com/open?id=1wLtc9nVhMuHOYfUafSzXuQCJKMdroGHm](https://drive.google.com/open?id=1wLtc9nVhMuHOYfUafSzXuQCJKMdroGHm).

Now the printer seems to be connected, but as soon as I click on "Scan", another communication problem message pops up: [https://drive.google.com/open?id=1copMXvLdhOAMjoSjMi-zNXhmwSyDVKK1](https://drive.google.com/open?id=1copMXvLdhOAMjoSjMi-zNXhmwSyDVKK1).

When I run hp-check, this is what I get: [https://drive.google.com/open?id=1AT4jAC1xiUmxXdW6YprVtOoofG5auyPv](https://drive.google.com/open?id=1AT4jAC1xiUmxXdW6YprVtOoofG5auyPv).

Printer is connected only via USB, no network or WiFI. I've actually seen it work this way (via USB) on my brother's Ubuntu.

What can I do? Thanks in advance!

---

### Post by tinylagarto on 2018-01-23
I have an HP printer and it works perfectly. But I use it via Wifi. Maybe you could try it with the Wifi option. I have no experience connecting a printer via USB.

---

### Post by pdc on 2018-01-23
so all a bit strange; as you seemed to get an initial message about a plug-in; but when I check on HP's list of which printers need plug-ins; it seems to say the J4660 does not need a plug-in; [https://developers.hp.com/hp-linux-imaging-and-printing/supported_devices/index](https://developers.hp.com/hp-linux-imaging-and-printing/supported_devices/index)

can I suggest you run ```
hp-plugin
``` from a terminal again; and if you could please copy the entire print-out that you get and PASTE it back here; that would give us the best chance of trying to help; 

then if you run ```
hp-check
``` as that is meant to look for dependencies etc; and again give us all the print-out

and then if you delete any existing entries from the PRINTERS folder; as it doesn't work; and maybe after giving us the info as above; if you do ```
hp-setup
``` again 

You seem to have done a very thorough job of checking the trouble-shooting page on hplip; much of their advice now seems to revolve around the above commands; 

______________

as you have likely added 3.17.11 to a system where 3.16.3 was already installed; this thread [https://forums.linuxmint.com/viewtopic.php?f=49&t=252338#p1357488](https://forums.linuxmint.com/viewtopic.php?f=49&t=252338#p1357488) from a very organised user on the Mint forum; talks about cleansing one's system of any remnants of 3.16.3 as he found the hplip installer did not actually do that; you might want to first of all work through Karl's advice and see if it sorts things for you; it all sounded very sensible what he suggested;

---

### Post by talestomaz on 2018-02-16
> **pdc said:**
> so all a bit strange; as you seemed to get an initial message about a plug-in; but when I check on HP's list of which printers need plug-ins; it seems to say the J4660 does not need a plug-in; [https://developers.hp.com/hp-linux-imaging-and-printing/supported_devices/index](https://developers.hp.com/hp-linux-imaging-and-printing/supported_devices/index)

can I suggest you run ```
hp-plugin
``` from a terminal again; and if you could please copy the entire print-out that you get and PASTE it back here; that would give us the best chance of trying to help; 

then if you run ```
hp-check
``` as that is meant to look for dependencies etc; and again give us all the print-out

and then if you delete any existing entries from the PRINTERS folder; as it doesn't work; and maybe after giving us the info as above; if you do ```
hp-setup
``` again 

You seem to have done a very thorough job of checking the trouble-shooting page on hplip; much of their advice now seems to revolve around the above commands; 

______________

as you have likely added 3.17.11 to a system where 3.16.3 was already installed; this thread [https://forums.linuxmint.com/viewtopic.php?f=49&t=252338#p1357488](https://forums.linuxmint.com/viewtopic.php?f=49&t=252338#p1357488) from a very organised user on the Mint forum; talks about cleansing one's system of any remnants of 3.16.3 as he found the hplip installer did not actually do that; you might want to first of all work through Karl's advice and see if it sorts things for you; it all sounded very sensible what he suggested;

Thanks a lot and sorry for the delay.

Tried the Mint forum thing. Didn't work. Then re-installed hplip the same way as before.

Here is what I get running the commands you suggested:

hp-plugin:
```
HP Linux Imaging and Printing System (ver. 3.17.11)
Plugin Download and Install Utility ver. 2.1

Copyright (c) 2001-15 HP Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.


HP Linux Imaging and Printing System (ver. 3.17.11)
Plugin Download and Install Utility ver. 2.1

Copyright (c) 2001-15 HP Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

Checking for network connection...
Downloading plug-in from: 
error: Plugin download failed with error code = 8
error:  file does not match its checksum. File may have been corrupted or altered

Done.

```

hp-check:
```
Saving output in log file: /home/ttomaz/hp-check.log

HP Linux Imaging and Printing System (ver. 3.17.11)
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

 Kernel: 4.4.0-112-generic #135-Ubuntu SMP Fri Jan 19 11:48:36 UTC 2018 GNU/Linux
 Host: tales-inspiron
 Proc: 4.4.0-112-generic #135-Ubuntu SMP Fri Jan 19 11:48:36 UTC 2018 GNU/Linux
 Distribution: 12 16.04
 Bitness: 64 bit


-----------------------
| HPLIP CONFIGURATION |
-----------------------

HPLIP-Version: HPLIP 3.17.11
HPLIP-Home: /usr/share/hplip
HPLIP-Installation: Auto installation is supported for ubuntu distro  16.04 version 

Current contents of '/etc/hp/hplip.conf' file:
# hplip.conf.  Generated from hplip.conf.in by configure.

[hplip]
version=3.17.11

[dirs]
home=/usr/share/hplip
run=/var/run
ppd=/usr/share/ppd/HP
ppdbase=/usr/share/ppd
doc=/usr/share/doc/hplip-3.17.11
html=/usr/share/doc/hplip-3.17.11
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
internal-tag=3.17.11
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
class-driver=no


Current contents of '/var/lib/hp/hplip.state' file:
Plugins are not installed. Could not access file: Arquivo ou diretório não encontrado

Current contents of '~/.hplip/hplip.conf' file:
[upgrade]
notify_upgrade = true
last_upgraded_time = 1518829966
pending_upgrade_time = 0

[installation]
date_time = 16/02/2018 23:20:44
version = 3.17.11


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

 scanext              Scan-SANE-Extension                                          REQUIRED        -               3.17.11         OK         -
 hpaio                HPLIP-SANE-Backend                                           REQUIRED        -               3.17.11         OK         'hpaio found in /etc/sane.d/dll.conf'

-------------------------
| External Dependencies |
-------------------------

 gs                   GhostScript - PostScript and PDF language interpreter and previewer REQUIRED        7.05            9.18            OK         -
 scanimage            scanimage - Shell scanning program                           OPTIONAL        1.0             1.0.25          OK         -
 cups                 CUPS - Common Unix Printing System                           REQUIRED        1.1             2.1.3           OK         'CUPS Scheduler is running'
 network              network -wget                                                OPTIONAL        -               1.17.1          OK         -
 policykit            PolicyKit - Administrative policy framework                  OPTIONAL        -               0.105           OK         -
 xsane                xsane - Graphical scanner frontend for SANE                  OPTIONAL        0.9             0.999           OK         -
 dbus                 DBus - Message bus system                                    REQUIRED        -               1.10.6          OK         -
 avahi-utils          avahi-utils                                                  OPTIONAL        -               0.6.32          OK         -

---------------------
| Python Extentions |
---------------------

 hpmudext             IO-Extension                                                 REQUIRED        -               3.17.11         OK         -
 cupsext              CUPS-Extension                                               REQUIRED        -               3.17.11         OK         -

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

 
Officejet_J4660
---------------
Type: Printer
Device URI: hp:/usb/Officejet_J4660_series?serial=BR24HGF0Q9052W
PPD: /etc/cups/ppd/Officejet_J4660.ppd
PPD Description: HP Officejet j4660 Series, hpcups 3.17.11
Printer status: printer Officejet_J4660 is idle.  enabled since Sex 16 Fev 2018 18:50:39 -02
error: Unable to communicate with device (code=12): hp:/usb/Officejet_J4660_series?serial=BR24HGF0Q9052W
error: Device not found
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

```

About the last step ("deleting entries from the Printer folder"), what is this about? Where is this folder?

I'd appreciate any advice! :D

---

### Post by Tony_Bennett on 2018-02-17
this link  [https://bugs.launchpad.net/hplip/+bug/1749573](https://bugs.launchpad.net/hplip/+bug/1749573)
(see #3 posting) indicates the site used to download plugins is offline...
... so just download the plugin from this site [http://www.openprinting.org/download/printdriver/auxfiles/HP/plugins/](http://www.openprinting.org/download/printdriver/auxfiles/HP/plugins/)   
and "run" the file. (assuming you are installing 3.17.11, the plugin you need is hplip-3.17.11-plugin.run )...
Or use "hp-plugin" and specify the path to the file you've downloaded... thereby eliminating the need for hp-plugin
to "download" it.

---

### Post by talestomaz on 2018-02-20
> **Tony_Bennett said:**
> this link  [https://bugs.launchpad.net/hplip/+bug/1749573](https://bugs.launchpad.net/hplip/+bug/1749573)
(see #3 posting) indicates the site used to download plugins is offline...
... so just download the plugin from this site [http://www.openprinting.org/download/printdriver/auxfiles/HP/plugins/](http://www.openprinting.org/download/printdriver/auxfiles/HP/plugins/)   
and "run" the file. (assuming you are installing 3.17.11, the plugin you need is hplip-3.17.11-plugin.run )...
Or use "hp-plugin" and specify the path to the file you've downloaded... thereby eliminating the need for hp-plugin
to "download" it.

Thanks! I've just done that, the plugin was successfully installed, but even so my printer still doesn't work. The same problem of not finding the device (or communication problem) persists, popping up messages exactly like the ones I mentioned in my first message. Sometimes (after many refreshes) it does recognize a connection with the printer, but it is lost as soon as I try to do something (print, scan etc.).

I had suspected that the problem might be in the cable, then I ordered a brand new USB cable. Made no difference. Same communication problems. (By the way, the printer seems to run exclusively via USB, no Wi-Fi, therefore).

This is what I get when I run hp-check now (after successfully installing the plugin as indicated above):

```
Saving output in log file: /home/ttomaz/hp-check.log

HP Linux Imaging and Printing System (ver. 3.17.11)
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

 Kernel: 4.4.0-112-generic #135-Ubuntu SMP Fri Jan 19 11:48:36 UTC 2018 GNU/Linux
 Host: tales-inspiron
 Proc: 4.4.0-112-generic #135-Ubuntu SMP Fri Jan 19 11:48:36 UTC 2018 GNU/Linux
 Distribution: 12 16.04
 Bitness: 64 bit


-----------------------
| HPLIP CONFIGURATION |
-----------------------

HPLIP-Version: HPLIP 3.17.11
HPLIP-Home: /usr/share/hplip
HPLIP-Installation: Auto installation is supported for ubuntu distro  16.04 version 

Current contents of '/etc/hp/hplip.conf' file:
# hplip.conf.  Generated from hplip.conf.in by configure.

[hplip]
version=3.17.11

[dirs]
home=/usr/share/hplip
run=/var/run
ppd=/usr/share/ppd/HP
ppdbase=/usr/share/ppd
doc=/usr/share/doc/hplip-3.17.11
html=/usr/share/doc/hplip-3.17.11
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
internal-tag=3.17.11
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
class-driver=no


Current contents of '/var/lib/hp/hplip.state' file:
[plugin]
installed = 1
eula = 1
version = 3.17.11



Current contents of '~/.hplip/hplip.conf' file:
[upgrade]
notify_upgrade = true
last_upgraded_time = 1518829966
pending_upgrade_time = 0
latest_available_version = 3.17.10

[installation]
date_time = 20/02/2018 10:07:25
version = 3.17.11

[settings]
systray_visible = 0
systray_messages = 0

[last_used]
device_uri = "hp:/usb/Officejet_J4660_series?serial=0"
printer_name = 
working_dir = /home/ttomaz/Downloads/hplip-3.17.11/hplip-3.17.11-plugin.run

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

 scanext              Scan-SANE-Extension                                          REQUIRED        -               3.17.11         OK         -
 hpaio                HPLIP-SANE-Backend                                           REQUIRED        -               3.17.11         OK         'hpaio found in /etc/sane.d/dll.conf'

-------------------------
| External Dependencies |
-------------------------

 gs                   GhostScript - PostScript and PDF language interpreter and previewer REQUIRED        7.05            9.18            OK         -
 scanimage            scanimage - Shell scanning program                           OPTIONAL        1.0             1.0.25          OK         -
 cups                 CUPS - Common Unix Printing System                           REQUIRED        1.1             2.1.3           OK         'CUPS Scheduler is running'
 network              network -wget                                                OPTIONAL        -               1.17.1          OK         -
 policykit            PolicyKit - Administrative policy framework                  OPTIONAL        -               0.105           OK         -
 xsane                xsane - Graphical scanner frontend for SANE                  OPTIONAL        0.9             0.999           OK         -
 dbus                 DBus - Message bus system                                    REQUIRED        -               1.10.6          OK         -
 avahi-utils          avahi-utils                                                  OPTIONAL        -               0.6.32          OK         -

---------------------
| Python Extentions |
---------------------

 hpmudext             IO-Extension                                                 REQUIRED        -               3.17.11         OK         -
 cupsext              CUPS-Extension                                               REQUIRED        -               3.17.11         OK         -

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

 
Officejet_J4660
---------------
Type: Printer
Device URI: hp:/usb/Officejet_J4660_series?serial=0
PPD: /etc/cups/ppd/Officejet_J4660.ppd
PPD Description: HP Officejet j4660 Series, hpcups 3.17.11
Printer status: printer Officejet_J4660 is idle.  enabled since Ter 20 Fev 2018 10:06:24 -03
error: Unable to communicate with device (code=12): hp:/usb/Officejet_J4660_series?serial=0
error: Device not found
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

```

Any hint?

---

### Post by pdc on 2018-02-20
phew; all one can suggest is to delete the existing entry from the PRINTERS folder

then run ```
hp-setup
``` from the terminal; ........... that makes hplip have another go at registering the device .........

_____________

I wondered which version of hplip you are using; I ask because a user on the Mint forum found that when one deleted earlier versions of hplip, they did not disappear entirely ........ I think it was mainly the scanning side ... but I thought to mention it 

[https://forums.linuxmint.com/viewtopic.php?f=49&t=252338#p1357488](https://forums.linuxmint.com/viewtopic.php?f=49&t=252338#p1357488)

______________

one sees these reports with hplip where hplip does not "see" what should be visible .......... one can only report it to HP as a bug or an issue ............ again, one would need to google how to report issues ....

___________

if you do ```
lsusb
``` I am wondering if it is reported OK; and I wonder if you have some high-speed usb3 ports; or some usb hub; some folks have reported a direct connection to an old usb2 port has worked for some ...........

---

### Post by talestomaz on 2018-02-23
I am aware of this discussion on the Mint forum. I have done the whole procedure to eliminate older versions. As long as I can see, there is only one version of HPLIP installed, the most recent one.

I've just done the other suggestion you gave, deleting previous printer files in etc/cups/ppd and folders hplip and sane in home. Then run hp-setup. It doesn't find the device, although it is connected, the same way as before. I imagine that, if I refresh it many times, it will finally find the device, but it won't ultimately work, exactly as before. It seems like one in 30 times it finds the way to the printer, but that is not enough for it to work.

Ok, lsusb:

```
ttomaz@tales-inspiron:~$ lsusb
Bus 001 Device 006: ID 064e:812e Suyin Corp. 
Bus 001 Device 005: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 004: ID 04f3:0034 Elan Microelectronics Corp. 
Bus 001 Device 007: ID 0cf3:0036 Atheros Communications, Inc. 
Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 002: ID 046d:c52f Logitech, Inc. Unifying Receiver
Bus 002 Device 003: ID 090c:1000 Silicon Motion, Inc. - Taiwan (formerly Feiya Technology Corp.) Flash Drive
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

That's it.

---

### Post by pdc on 2018-02-23
my take on the fact that it is not seen in lsusb ............... 

...... (assuming printer plugged in; turned on etc ........)

..... is that this is a hardware issue ...... do you know if some of the ports are usb3 etc ....... sometimes that can be a problem ..

....... do you have usb hubs running there ...... folks often suggest a direct usb connection to an older usb2 port .......... sorry if this all seems painfully pedestrian ... sometimes folks report they get a new usb cable and bingo ... etc sorry it is all "shots in the dark .." ........

---

