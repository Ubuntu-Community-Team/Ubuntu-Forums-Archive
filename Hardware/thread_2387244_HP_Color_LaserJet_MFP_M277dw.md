---
title: "HP Color LaserJet MFP M277dw"
date: 2018-03-16
forum: Hardware
---

### Post by favetella on 2018-03-16
Hi to all,

I have got a problem with my printer. I've installed it using the installer version HPLIP-3.18.3 but I'm able to access neither the printer, nor the scanner.
Here it is the Self Diagnose Utility output. What else should I do?

Thanks and best regards.

```
HP Linux Imaging and Printing System (ver. 3.18.3)
Self Diagnse Utility and Healing Utility ver. 1.0

Copyright (c) 2001-15 HP Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.


HP Linux Imaging and Printing System (ver. 3.18.3)
Self Diagnse Utility and Healing Utility ver. 1.0

Copyright (c) 2001-15 HP Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

 

Checking for Deprecated items....
No Deprecated items are found


Checking for HPLIP updates....

HP Linux Imaging and Printing System (ver. 3.18.3)
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

 Kernel: 4.13.0-37-generic #42-Ubuntu SMP Wed Mar 7 14:13:23 UTC 2018 GNU/Linux
 Host: manolo-Aspire-5735
 Proc: 4.13.0-37-generic #42-Ubuntu SMP Wed Mar 7 14:13:23 UTC 2018 GNU/Linux
 Distribution: 12 17.10
 Bitness: 64 bit


-----------------------
| HPLIP CONFIGURATION |
-----------------------

HPLIP-Version: HPLIP 3.18.3
HPLIP-Home: /usr/share/hplip
HPLIP-Installation: Auto installation is supported for ubuntu distro  17.10 version 

Current contents of '/etc/hp/hplip.conf' file:
# hplip.conf.  Generated from hplip.conf.in by configure.

[hplip]
version=3.18.3

[dirs]
home=/usr/share/hplip
run=/var/run
ppd=/usr/share/ppd/HP
ppdbase=/usr/share/ppd
doc=/usr/share/doc/hplip-3.18.3
html=/usr/share/doc/hplip-3.18.3
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
internal-tag=3.18.3
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
Plugins are not installed. Could not access file: File o directory non esistente

Current contents of '~/.hplip/hplip.conf' file:
[installation]
date_time = 16/03/2018 17:28:51
version = 3.18.3

[upgrade]
notify_upgrade = true
last_upgraded_time = 1521189416
pending_upgrade_time = 0
latest_available_version = 3.17.10

[settings]
systray_visible = 0
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

--------------
| COMPILEDEP |
--------------

 gcc                  gcc - GNU Project C and C++ Compiler                         REQUIRED        -               7.2.0           OK         -
 make                 make - GNU make utility to maintain groups of programs       REQUIRED        3.0             4.1             OK         -
 libtool              libtool - Library building support services                  REQUIRED        -               2.4.6           OK         -

------------------------
| General Dependencies |
------------------------

 libcrypto            libcrypto - OpenSSL cryptographic library                    REQUIRED        -               1.0.2           OK         -
 python-xml           Python XML libraries                                         REQUIRED        -               2.2.3           OK         -
 libnetsnmp-devel     libnetsnmp-devel - SNMP networking library development files REQUIRED        5.0.9           5.7.3           OK         -
 sane-devel           SANE - Scanning library development files                    REQUIRED        -               -               OK         -
 pil                  PIL - Python Imaging Library (required for commandline scanning with hp-scan) OPTIONAL        -               1.1.7           OK         -
 pyqt4-dbus           PyQt 4 DBus - DBus Support for PyQt4                         REQUIRED        4.0             4.11.4          OK         -
 libpthread           libpthread - POSIX threads library                           REQUIRED        -               2.26            OK         -
 python-devel         Python devel - Python development files                      REQUIRED        2.2             2.7.14          OK         -
 cups-devel           CUPS devel- Common Unix Printing System development files    REQUIRED        -               2.2.4           OK         -
 python-dbus          Python DBus - Python bindings for DBus                       REQUIRED        0.80.0          1.2.4           OK         -
 cups-ddk             CUPS DDK - CUPS driver development kit                       OPTIONAL        -               -               OK         -
 reportlab            Reportlab - PDF library for Python                           OPTIONAL        2.0             3.4.0           OK         -
 pyqt4                PyQt 4- Qt interface for Python (for Qt version 4.x)         REQUIRED        4.0             4.11.4          OK         -
 libusb               libusb - USB library                                         REQUIRED        -               1.0             OK         -
 cups-image           CUPS image - CUPS image development files                    REQUIRED        -               2.2.4           OK         -
 python2X             Python 2.2 or greater - Python programming language          REQUIRED        2.2             2.7.14          OK         -
 python-notify        Python libnotify - Python bindings for the libnotify Desktop notifications OPTIONAL        -               -               OK         -
 libjpeg              libjpeg - JPEG library                                       REQUIRED        -               -               OK         -
 sane                 SANE - Scanning library                                      REQUIRED        -               -               OK         -

----------------------
| Scan Configuration |
----------------------

 scanext              Scan-SANE-Extension                                          REQUIRED        -               3.18.3          OK         -
 hpaio                HPLIP-SANE-Backend                                           REQUIRED        -               3.18.3          OK         'hpaio found in /etc/sane.d/dll.conf'

-------------------------
| External Dependencies |
-------------------------

 gs                   GhostScript - PostScript and PDF language interpreter and previewer REQUIRED        7.05            9.21            OK         -
 scanimage            scanimage - Shell scanning program                           OPTIONAL        1.0             1.0.27          OK         -
 cups                 CUPS - Common Unix Printing System                           REQUIRED        1.1             2.2.4           OK         'CUPS Scheduler is running'
 network              network -wget                                                OPTIONAL        -               1.19.1          OK         -
 policykit            PolicyKit - Administrative policy framework                  OPTIONAL        -               0.105           OK         -
 xsane                xsane - Graphical scanner frontend for SANE                  OPTIONAL        0.9             0.999           OK         -
 dbus                 DBus - Message bus system                                    REQUIRED        -               1.10.22         OK         -
 avahi-utils          avahi-utils                                                  OPTIONAL        -               0.6.32          OK         -

---------------------
| Python Extentions |
---------------------

 hpmudext             IO-Extension                                                 REQUIRED        -               3.18.3          OK         -
 cupsext              CUPS-Extension                                               REQUIRED        -               3.18.3          OK         -

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

 
Hewlett-Packard_HP_Color_LaserJet_MFP_M277dw
--------------------------------------------
Type: Unknown
Device URI: dnssd://HP%20Color%20LaserJet%20MFP%20M277dw%20(24CE71)._ipp._tcp.local/?uuid=564e4238-4b33-5234-595a-3c528224ce71
PPD: /etc/cups/ppd/Hewlett-Packard_HP_Color_LaserJet_MFP_M277dw.ppd
**warning: Failed to read /etc/cups/ppd/Hewlett-Packard_HP_Color_LaserJet_MFP_M277dw.ppd ppd file**
PPD Description: 
Printer status: la stampante Hewlett-Packard_HP_Color_LaserJet_MFP_M277dw è inattiva.  è stata abilitata da sab 10 mar 2018 07:10:19 CET
**warning: Printer is not HPLIP installed. Printers must use the hp: or hpfax: CUPS backend for HP-Devices.**

HP_Color_LaserJet_MFP_M277dw
----------------------------
Type: Unknown
Device URI: socket://192.168.1.183
PPD: /etc/cups/ppd/HP_Color_LaserJet_MFP_M277dw.ppd
**warning: Failed to read /etc/cups/ppd/HP_Color_LaserJet_MFP_M277dw.ppd ppd file**
PPD Description: 
Printer status: la stampante HP_Color_LaserJet_MFP_M277dw è inattiva.  è stata abilitata da ven 16 mar 2018 15:44:53 CET
**warning: Printer is not HPLIP installed. Printers must use the hp: or hpfax: CUPS backend for HP-Devices.**


--------------
| PERMISSION |
--------------

 

Checking Permissions....


Checking for Configured Queues....
[B]warning: Fail to read ppd=/etc/cups/ppd/Hewlett-Packard_HP_Color_LaserJet_MFP_M277dw.ppd file
warning: Insufficient permission to access file /etc/cups/ppd/Hewlett-Packard_HP_Color_LaserJet_MFP_M277dw.ppd
warning: Could not complete Queue(s) configuration check[/B]


Checking for HP Properitery Plugin's....
No plug-in printers are configured.
 
Diagnose completed...



More information on Troubleshooting,How-To's and Support is available on http://hplipopensource.com/hplip-web/index.html


Please close this terminal manually. 
```

---

### Post by Autodave on 2018-03-16
Are we to assume that you are using this wirelessly? I have the same printer and have no issues at all with it working wirelessly. Did you enable it through the printer itself? (I seem to remember having to do that.)

---

### Post by pdc on 2018-03-16
so that needs 3.15.3 of hplip .... so you are well ahead with 3.18.3             ......... it has leapt rapidly from 3.17.11 ........

________

anything with an MFP seems to need a plug-in ... this one certainly does .... from here .....  [https://developers.hp.com/hp-linux-imaging-and-printing/supported_devices/index](https://developers.hp.com/hp-linux-imaging-and-printing/supported_devices/index)

____________-

here is the HP page on plug-ins [https://developers.hp.com/hp-linux-imaging-and-printing/binary_plugin.html](https://developers.hp.com/hp-linux-imaging-and-printing/binary_plugin.html)

______

so they would say ...... open a terminal ......... type ```
hp-setup
```        and that should set up the printer; and as part of its run, install the needed plug-in

_____
I think what AutoDave is saying is you sometimes have to start with a usb connection, even if wireless is the long-term; that was so for us: for our OfficeJet, it would initally not connect to the router; then with usb, all seemed to happen behind the scenes; and we were wireless ........

---

### Post by favetella on 2018-03-16
> **Autodave said:**
> Are we to assume that you are using this wirelessly? I have the same printer and have no issues at all with it working wirelessly. Did you enable it through the printer itself? (I seem to remember having to do that.)
Yes, you assume right: wirelessly. Sorry for not specifying that before. However, I did set it up from the printer itself. In fact, I had the printer drivers correctly working but the scanner did not work. When I tried to use the scanner through Xsane or Gimp (calling in turn xsane too together with a couple of more options) or other clients I had an error telling me about the missing plugin. When I tried to install the plugin I got the error that I'm going to show in my next reply to Mr/Ms pdc.

---

### Post by favetella on 2018-03-16
> **pdc said:**
> 
so they would say ...... open a terminal ......... type ```
hp-setup
```        and that should set up the printer; and as part of its run, install the needed plug-in


I don't know whether you're just suggesting me to run hp-setup only or any other things too, but this was the original problem I got when I tried to install the plugins to make the scanner work.

```
hp-setup
Traceback (most recent call last):
  File "/usr/bin/hp-setup", line 48, in <module>
    from base import device, utils, tui, models, module, services, os_utils
  File "/usr/share/hplip/base/device.py", line 42, in <module>
    from . import status
  File "/usr/share/hplip/base/status.py", line 33, in <module>
    import cupsext
ImportError: libusb-1.0.so.0: failed to map segment from shared object
```

After purging the hplip installation, removing several directories as suggested in a forum page (*I'll post it as soon as I find it back*) and reinstalling everything from scratch the problem persists.

First of all, is running *sh hplip-3.18.3.run* enough to say I've correctly installed what it's required to make the printer/scanner work correctly?

What should I do now anyway?

Thanks for your support and best regards.

---

### Post by thehipho on 2018-03-16
Did you use Scanimage to check whether it's able to find your scanner? ```
scanimage -L
```

---

### Post by pdc on 2018-03-16
thanks; gosh, where all the hp-fanboys when you want them? There are enthusiasts who say .... just get HP .... it always works ........

reading the HP documentation ........ you could try ```
hp-plugin
```

____________

there is a distro called Mint; it is derived from Ubuntu; on their forum, one of the experienced users reported on his experience of installing newer versions of hplip; as I understood him, the newer version FAILED to get rid of all the old stuff; for scanning; 

so in this thread [https://forums.linuxmint.com/viewtopic.php?t=262172](https://forums.linuxmint.com/viewtopic.php?t=262172) he backgrounds things ..... and points you to this [https://forums.linuxmint.com/viewtopic.php?f=49&t=252338#p1357488](https://forums.linuxmint.com/viewtopic.php?f=49&t=252338#p1357488)

Karl says there are 2 solutions: choose one or the other ...  I would suggest you do one or the other for your system ..

__________

I just wonder if you cleanse like he suggests; (so adding the latest 3.18.3 ) ........ then run ```
hp-check 
```    ..... that checks if all is good then if you have done a purge and a clean install, if you do ```
hp-setup
``` that should also pull the plug-in ........

and so should register the printer with lpadmin and it ...... should ...... then work ..

_________

I remember reading some folks had issues with getting plug-ins a few weeks ago; something to do with websites being down; and so sourcing plug-ins from somewhere else ... we hope all that is sorted now 

_________

I hope somehow; somewhere; in the above; is a clear path for you to follow!

---

### Post by favetella on 2018-03-18
> **thehipho said:**
> Did you use Scanimage to check whether it's able to find your scanner? ```
scanimage -L
```

I get the following response
```
manolo@manolo-Aspire-5735:~$ scanimage -L

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).

```
 
together with the following popup message:

> HPLIP cannot detect devices in your network. This may be due to existing firewall settings blocking the required ports like (5353/udp). When you are in a trusted network environment, you may open the ports for network services like mdns and slp in the firewall. For detailed steps follow the link.

[http://hplipopensource.com/node/375](http://hplipopensource.com/node/375)


Then I've been following the suggestion to run sane-find-scanner tool.

```
manolo@manolo-Aspire-5735:~$ sane-find-scanner

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

  # No USB scanners found. If you expected something different, make sure that
  # you have loaded a kernel driver for your USB host controller and have setup
  # the USB system correctly. See man sane-usb for details.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as
  # necessary.
manolo@manolo-Aspire-5735:~$ sudo sane-find-scanner
[sudo] password di manolo: 

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

could not fetch string descriptor (again): Overflow
  # No USB scanners found. If you expected something different, make sure that
  # you have loaded a kernel driver for your USB host controller and have setup
  # the USB system correctly. See man sane-usb for details.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.
```

---

### Post by favetella on 2018-03-18
> **pdc said:**
> thanks; gosh, where all the hp-fanboys when you want them? There are enthusiasts who say .... just get HP .... it always works ........

reading the HP documentation ........ you could try ```
hp-plugin
```

```


manolo@manolo-Aspire-5735:~$ hp-plugin
Traceback (most recent call last):
  File "/usr/bin/hp-plugin", line 41, in <module>
    from base import device, utils, tui, module, services
  File "/usr/share/hplip/base/device.py", line 42, in <module>
    from . import status
  File "/usr/share/hplip/base/status.py", line 33, in <module>
    import cupsext
ImportError: libusb-1.0.so.0: failed to map segment from shared object
manolo@manolo-Aspire-5735:~$ sudo hp-plugin
Traceback (most recent call last):
  File "/usr/bin/hp-plugin", line 41, in <module>
    from base import device, utils, tui, module, services
  File "/usr/share/hplip/base/device.py", line 42, in <module>
    from . import status
  File "/usr/share/hplip/base/status.py", line 33, in <module>
    import cupsext
ImportError: libusb-1.0.so.0: failed to map segment from shared object

```

> 
____________

there is a distro called Mint; it is derived from Ubuntu; on their forum, one of the experienced users reported on his experience of installing newer versions of hplip; as I understood him, the newer version FAILED to get rid of all the old stuff; for scanning; 

so in this thread [https://forums.linuxmint.com/viewtopic.php?t=262172](https://forums.linuxmint.com/viewtopic.php?t=262172) he backgrounds things ..... and points you to this [https://forums.linuxmint.com/viewtopic.php?f=49&t=252338#p1357488](https://forums.linuxmint.com/viewtopic.php?f=49&t=252338#p1357488)

Karl says there are 2 solutions: choose one or the other ...  I would suggest you do one or the other for your system ..

I've been firstly following the suggestion aimed to manually clean any previous installation and then reinstall. Unfortunately the problem persists and I take advantage of this reply to remark that I'm not able to use my device at all: neither the printer, nor the scanner. This is the result after reinstalling the drivers (or whatever they are) after downloading the latest version of the package from the official website.

```

 ./hplip-3.18.3.run
Creating directory hplip-3.18.3
Verifying archive integrity... All good.
Uncompressing HPLIP 3.18.3 Self Extracting Archive...................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................chown: cambiamento del proprietario di './.libs/libhpmud.so.0.0.6T': Operazione non permessa
chown: cambiamento del proprietario di './.libs/hpmudext.soT': Operazione non permessa
chown: cambiamento del proprietario di './.libs/libsane-hpaio.so.1.0.0T': Operazione non permessa
chown: cambiamento del proprietario di './.libs/cupsext.soT': Operazione non permessa
chown: cambiamento del proprietario di './.libs/libhpipp.so.0.0.1T': Operazione non permessa
chgrp: cambiamento del gruppo di './.libs/libhpmud.so.0.0.6T': Operazione non permessa
chgrp: cambiamento del gruppo di './.libs/hpmudext.soT': Operazione non permessa
chgrp: cambiamento del gruppo di './.libs/libsane-hpaio.so.1.0.0T': Operazione non permessa
chgrp: cambiamento del gruppo di './.libs/cupsext.soT': Operazione non permessa
chgrp: cambiamento del gruppo di './.libs/libhpipp.so.0.0.1T': Operazione non permessa


HP Linux Imaging and Printing System (ver. 3.18.3)
HPLIP Installer ver. 5.1

Copyright (c) 2001-15 HP Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

Installer log saved in: hplip-install_Sun-18-Mar-2018_21:06:25.log

\
note: Defaults for each question are maked with a '*'. Press <enter> to accept the default.
 

INSTALLATION MODE
-----------------
Automatic mode will install the full HPLIP solution with the most common options.
Custom mode allows you to choose installation options to fit specific requirements.

Please choose the installation mode (a=automatic*, c=custom, q=quit) : a


INTRODUCTION
------------
This installer will install HPLIP version 3.18.3 on your computer.
Please close any running package management systems now (YaST, Adept, Synaptic, Up2date, etc).


DISTRO/OS CONFIRMATION
----------------------
Distro appears to be Ubuntu 17.10.

Is "Ubuntu 17.10" your correct distro/OS and version (y=yes*, n=no, q=quit) ? n


DISTRO/OS SELECTION
-------------------

Choose the name of the distro/OS that most closely matches your system:

Num.  Distro/OS Name          
----  ------------------------
0     Mepis                   
1     Debian                  
2     SUSE Linux              
3     Mandriva Linux          
4     Fedora                  
5     Red Hat                 
6     Red Hat Enterprise Linux
7     Ubuntu                  
8     PCLinuxOS               
9     Linux Mint              
10    gOS                     
11    Linpus Linux            
12    Manjaro Linux           
13    IGOS                    
14    Boss                    
15    Linux From Scratch      

Enter number 0...15 (q=quit) ?7

Choose the version of "Ubuntu" that most closely matches your system:

Num.  Distro/OS Version                       
----  ----------------------------------------
0     Unknown or not listed                   
1     12.04 ("Precise", Released 28/04/2012)  
2     13.10 ("Saucy", Released 17/10/2013)    
3     14.04 ("Trusty", Released 17/04/2014)   
4     15.04 ("Vivid", Released 17/04/2015)    
5     15.10 ("Willy", Released 22/10/2015)    
6     16.04 ("Xenial", Released 17/04/2016)   
7     16.10 ("Yakkety", Released 13/10/2016)  
8     17.04 ("Zesty", Released 31/05/2017)    
9     17.10 ("Artful Aardvark", Released      
      19/10/2017)                             

Enter number 0...9 (q=quit) ?9

Distro set to: Ubuntu 17.10

Initializing. Please wait...


ENTER USER PASSWORD
-------------------
Please enter the sudoer (manolo)'s password: 
 

INSTALLATION NOTES
------------------
Enable the universe/multiverse repositories. Also be sure you are using the Ubuntu "Main" Repositories. See: https://help.ubuntu.com/community/Repositories/Ubuntu for more information.  Disable the CD-ROM/DVD source if you do not have the Ubuntu installation media inserted in the drive.

Please read the installation notes. Press <enter> to continue or 'q' to quit: 


SECURITY PACKAGES
-----------------
AppArmor is installed. 
AppArmor protects the application from external intrusion attempts making the application secure

Would you like to have this installer install the hplip specific policy/profile (y=yes*, n=no, q=quit) ? 


RUNNING PRE-INSTALL COMMANDS
----------------------------
OK


CHECKING FOR NETWORK CONNECTION
-------------------------------
Network connection present.


RUNNING PRE-PACKAGE COMMANDS
----------------------------
sudo dpkg --configure -a (Pre-depend step 1)
sudo apt-get install --yes --force-yes -f (Pre-depend step 2)
sudo apt-get update (Pre-depend step 3)
OK


DEPENDENCY AND CONFLICT RESOLUTION
----------------------------------
HPLIP-3.18.3 exists, this may conflict with the new one being installed.
Do you want to ('i'= Remove and Install*, 'q'= Quit)?    :i
Starting uninstallation...
HPLIP uninstallation is completed


RUNNING POST-PACKAGE COMMANDS
-----------------------------
OK


RE-CHECKING DEPENDENCIES
------------------------
OK


PRE-BUILD COMMANDS
------------------
OK


BUILD AND INSTALL
-----------------
Running './configure --with-hpppddir=/usr/share/ppd/HP --libdir=/usr/lib --prefix=/usr --enable-qt4 --disable-qt5 --enable-doc-build --disable-cups-ppd-install --disable-foomatic-drv-install --disable-libusb01_build --disable-foomatic-ppd-install --disable-hpijs-install --disable-class-driver --disable-udev_sysfs_rules --disable-policykit --enable-cups-drv-install --enable-hpcups-install --enable-network-build --enable-dbus-build --enable-scan-build --enable-fax-build --enable-apparmor_build'
Please wait, this may take several minutes...
Command completed successfully.

Running 'make clean'
Please wait, this may take several minutes...
Command completed successfully.

Running 'make'
Please wait, this may take several minutes...
Command completed successfully.

Running 'sudo make install'
Please wait, this may take several minutes...
Command completed successfully.


Build complete.



POST-BUILD COMMANDS
-------------------
 

CLOSE HP_SYSTRAY
----------------
Sending close message to hp-systray (if it is currently running)...
OK


HPLIP UPDATE NOTIFICATION
-------------------------
Do you want to check for HPLIP updates?. (y=yes*, n=no) : y


RESTART OR RE-PLUG IS REQUIRED
------------------------------
If you are installing a USB connected printer, and the printer was plugged in when you started this installer, you will need to either restart your PC or unplug and re-plug in your printer    
(USB cable only). If you choose to restart, run this command after restarting: hp-setup (Note: If you are using a parallel connection, you will have to restart your PC. If you are using       
network/wireless, you can ignore and continue).                                                                                                                                                 

Restart or re-plug in your printer (r=restart, p=re-plug in*, i=ignore/continue, q=quit) : i


PRINTER SETUP
-------------
Please make sure your printer is connected and powered on at this time.
[B]Do you want to setup printer in GUI mode? (u=GUI mode*, i=Interactive mode) : i
Running 'hp-setup  -i' command....
Traceback (most recent call last):
  File "/usr/bin/hp-setup", line 48, in <module>
    from base import device, utils, tui, models, module, services, os_utils
  File "/usr/share/hplip/base/device.py", line 42, in <module>
    from . import status
  File "/usr/share/hplip/base/status.py", line 33, in <module>
    import cupsext
ImportError: libusb-1.0.so.0: failed to map segment from shared object
error: hp-setup failed. Please run hp-setup manually.[/B]


RE-STARTING HP_SYSTRAY
----------------------

HP Linux Imaging and Printing System (ver. 3.18.3)
System Tray Status Service ver. 2.0

Copyright (c) 2001-15 HP Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

/usr/lib/python2.7/dist-packages/gtk-2.0/gtk/__init__.py:127: RuntimeWarning: PyOS_InputHook is not available for interactive use of PyGTK
  set_interactive(1)


```

The error marked in bold is what I usually get when running different hp printer/scanner tools to install the plugin, check the installation or others. I'll show it up as long as I'm describing the tests made to solve he problem. Two more details: that error with the above command appears when both selecting the interactive or the gui mode; I'm using Kubuntu 17.10 which is not included in the list, so I selected Ubuntu 17.10 which was the autodetected choice anyway.

> __________

I just wonder if you cleanse like he suggests; (so adding the latest 3.18.3 ) ........ then run ```
hp-check 
```    ..... that checks if all is good then if you have done a purge and a clean install, if you do ```
hp-setup
``` that should also pull the plug-in ........

and so should register the printer with lpadmin and it ...... should ...... then work ..

_________ 

The hp-check gave me some hints.
```

manolo@manolo-Aspire-5735:~/Scrivania$ hp-check 
Saving output in log file: /home/manolo/Scrivania/hp-check.log

HP Linux Imaging and Printing System (ver. 3.17.7)
Dependency/Version Check Utility ver. 15.1

Copyright (c) 2001-15 HP Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

Note: hp-check can be run in three modes:
1. Compile-time check mode (-c or --compile): Use this mode before compiling the HPLIP supplied tarball (.tar.gz or .run) to determine if the proper dependencies are installed to successfully 
compile HPLIP.                                                                                                                                                                                  
2. Run-time check mode (-r or --run): Use this mode to determine if a distro supplied package (.deb, .rpm, etc) or an already built HPLIP supplied tarball has the proper dependencies installed
to successfully run.                                                                                                                                                                            
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

warning: 12-17.10 version is not supported. Using 12-17.04 versions dependencies to verify and install...

---------------
| SYSTEM INFO |
---------------

 Kernel: 4.13.0-37-generic #42-Ubuntu SMP Wed Mar 7 14:13:23 UTC 2018 GNU/Linux
 Host: manolo-Aspire-5735
 Proc: 4.13.0-37-generic #42-Ubuntu SMP Wed Mar 7 14:13:23 UTC 2018 GNU/Linux
 Distribution: 12 17.10
 Bitness: 64 bit


-----------------------
| HPLIP CONFIGURATION |
-----------------------

HPLIP-Version: HPLIP 3.17.7
HPLIP-Home: /usr/share/hplip
warning: HPLIP-Installation: Auto installation is not supported for 12 distro  17.10 version 

Current contents of '/etc/hp/hplip.conf' file:
# hplip.conf.  Generated from hplip.conf.in by configure.

[hplip]
version=3.17.7

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
internal-tag=3.17.7
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


Current contents of '/var/lib/hp/hplip.state' file:
Plugins are not installed. Could not access file: No such file or directory

Current contents of '~/.hplip/hplip.conf' file:
[upgrade]
notify_upgrade = true
last_upgraded_time = 1521404467
pending_upgrade_time = 0

[installation]
date_time = 03/18/18 21:42:12
version = 3.17.7


 <Package-name>        <Package-Desc>      <Required/Optional> <Min-Version> <Installed-Version> <Status>   <Comment>

-------------------------
| External Dependencies |
-------------------------

 cups                 CUPS - Common Unix Printing System                           REQUIRED        1.1             2.2.4           OK         'CUPS Scheduler is running'
 gs                   GhostScript - PostScript and PDF language interpreter and previewer REQUIRED        7.05            9.21            OK         -
 xsane                xsane - Graphical scanner frontend for SANE                  OPTIONAL        0.9             0.999           OK         -
 scanimage            scanimage - Shell scanning program                           OPTIONAL        1.0             1.0.27          OK         -
 dbus                 DBus - Message bus system                                    REQUIRED        -               1.10.22         OK         -
 policykit            PolicyKit - Administrative policy framework                  OPTIONAL        -               0.105           OK         -
 network              network -wget                                                OPTIONAL        -               1.19.1          OK         -
 avahi-utils          avahi-utils                                                  OPTIONAL        -               0.6.32          OK         -

------------------------
| General Dependencies |
------------------------

 libjpeg              libjpeg - JPEG library                                       REQUIRED        -               -               OK         -
 cups-devel           CUPS devel- Common Unix Printing System development files    REQUIRED        -               2.2.4           OK         -
 cups-image           CUPS image - CUPS image development files                    REQUIRED        -               2.2.4           OK         -
 libpthread           libpthread - POSIX threads library                           REQUIRED        -               b'2.26'         OK         -
 libusb               libusb - USB library                                         REQUIRED        -               1.0             OK         -
 sane                 SANE - Scanning library                                      REQUIRED        -               -               OK         -
 sane-devel           SANE - Scanning library development files                    REQUIRED        -               -               OK         -
 libnetsnmp-devel     libnetsnmp-devel - SNMP networking library development files REQUIRED        5.0.9           5.7.3           OK         -
 libcrypto            libcrypto - OpenSSL cryptographic library                    REQUIRED        -               1.0.2           OK         -
 python3X             Python 2.2 or greater - Python programming language          REQUIRED        2.2             3.6.3           OK         -
 python3-notify2      Python libnotify - Python bindings for the libnotify Desktop notifications OPTIONAL        -               -               OK         -
 error: python3-pyqt4-dbus PyQt 4 DBus - DBus Support for PyQt4                         OPTIONAL        4.0             -               MISSING    'python3-pyqt4-dbus needs to be installed'
 error: python3-pyqt4 PyQt 4- Qt interface for Python (for Qt version 4.x)         REQUIRED        4.0             -               MISSING    'python3-pyqt4 needs to be installed'
 python3-dbus         Python DBus - Python bindings for DBus                       REQUIRED        0.80.0          1.2.4           OK         -
 python3-xml          Python XML libraries                                         REQUIRED        -               2.2.3           OK         -
 error: python3-devel Python devel - Python development files                      REQUIRED        2.2             3.6.3           MISSING    'python3-devel needs to be installed'
 python3-pil          PIL - Python Imaging Library (required for commandline scanning with hp-scan) OPTIONAL        -               1.1.7           OK         -
 python3-reportlab    Reportlab - PDF library for Python                           OPTIONAL        2.0             3.4.0           OK         -

--------------
| COMPILEDEP |
--------------

 libtool              libtool - Library building support services                  REQUIRED        -               2.4.6           OK         -
 gcc                  gcc - GNU Project C and C++ Compiler                         REQUIRED        -               7.2.0           OK         -
 make                 make - GNU make utility to maintain groups of programs       REQUIRED        3.0             4.1             OK         -

---------------------
| Python Extentions |
---------------------

 cupsext              CUPS-Extension                                               REQUIRED        -               3.17.7          OK         -
 hpmudext             IO-Extension                                                 REQUIRED        -               3.17.7          OK         -

----------------------
| Scan Configuration |
----------------------

 hpaio                HPLIP-SANE-Backend                                           REQUIRED        -               3.17.7          OK         'hpaio found in /etc/sane.d/dll.conf'
 scanext              Scan-SANE-Extension                                          REQUIRED        -               3.17.7          OK         -

------------------------------
| DISCOVERED SCANNER DEVICES |
------------------------------

-error: HPLIP cannot detect devices in your network. This may be due to existing firewall settings blocking the required ports like (5353/udp). When you are in a trusted network environment, you may open the ports for network services like mdns and slp in the firewall. For detailed steps follow the link.

 http://hplipopensource.com/node/375
No Scanner found.

--------------------------
| DISCOVERED USB DEVICES |
--------------------------

No devices found.

---------------------------------
| INSTALLED CUPS PRINTER QUEUES |
---------------------------------

 

--------------
| PERMISSION |
--------------

 
-----------
| SUMMARY |
-----------

Missing Required Dependencies
-----------------------------
error: 'python3-pyqt4' package is missing/incompatible 
error: 'gtk2-engines-pixbuf' package is missing/incompatible 
error: 'python3-dev' package is missing/incompatible 

Missing Optional Dependencies
-----------------------------
error: 'python3-dbus.mainloop.qt' package is missing/incompatible 

Total Errors: 3
Total Warnings: 0


Done.


```

I've been correcting those errors and run hp-check again with no errors anymore. However the main problem persists.

```

 hp-setup
Traceback (most recent call last):
  File "/usr/bin/hp-setup", line 48, in <module>
    from base import device, utils, tui, models, module, services, os_utils
  File "/usr/share/hplip/base/device.py", line 41, in <module>
    from . import status
  File "/usr/share/hplip/base/status.py", line 32, in <module>
    import cupsext
ImportError: libusb-1.0.so.0: failed to map segment from shared object
Error in sys.excepthook:
Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/apport_python_hook.py", line 145, in apport_excepthook
    os.O_WRONLY | os.O_CREAT | os.O_EXCL, 0o640), 'wb') as f:
PermissionError: [Errno 13] Permission denied: '/var/crash/_usr_share_hplip_setup.py.1000.crash'

Original exception was:
Traceback (most recent call last):
  File "/usr/bin/hp-setup", line 48, in <module>
    from base import device, utils, tui, models, module, services, os_utils
  File "/usr/share/hplip/base/device.py", line 41, in <module>
    from . import status
  File "/usr/share/hplip/base/status.py", line 32, in <module>
    import cupsext
ImportError: libusb-1.0.so.0: failed to map segment from shared object



```  

and this happens when both running in user or root mode.

> I hope somehow; somewhere; in the above; is a clear path for you to follow!
I'm not sure, but I surely appreciate your support. Thank you so much.

---

### Post by pdc on 2018-03-18
I have noticed many problems with 17.10 ubuntu ....... with scanners mainly but printers also ..... Canon had to issue a new version of the UFR driver for all their lasers; to cope with whatever 17.10 threw up ...... HP have moved rapidly from 3.17.10 to 3.18.3 ... trying to keep up ...........

..... I can only hope that 18.04; which is meant to be LTS: ..... long-term support ....... will somehow have this stuff sorted ......... you might like to download whatever is the latest version of 18.04; put it on a usb stick; and see if you can configure hplip on it ..........

(I would suspect the hesitant will wisely wait for 18.04 to settle in before installing it too ............)

I think you need to file a bug report with Ubuntu .. and also with hplip ............. you would need to google on both ........

___________

I increasingly think the Mint stance; that most folks use the LTS as their base and stable platform; is the right one;

One can install the in-between versions of Ubuntu to evaluate them; in addition to a stable base install ............. and one needs to recognise the great work Ubuntu has done developing; innovating; pushing boundaries ........           great work in 14yrs   .. but that brings issues ............

...... so 16.04 was the last LTS ......but there have been updates to it .......... so 16.10 and 17.04 and 17.10 were all short-term; very short-term support releases ... and things are going to break in them ....... I suspect

---

### Post by chox_de on 2018-04-11
Saluti favetella,

I had the same symptoms with my M277dw over network from Ubuntu 14.04, with both the hplip-3.17.10 and hplip-3.18.3. The call of hp-setup always aborted with
```
hp-setup Traceback (most recent call last):
  File "/usr/bin/hp-setup", line 48, in <module>
    from base import device, utils, tui, models, module, services, os_utils
  File "/usr/share/hplip/base/device.py", line 42, in <module>
    from . import status
  File "/usr/share/hplip/base/status.py", line 33, in <module>
    import cupsext
ImportError: libusb-1.0.so.0: failed to map segment from shared object
```

At some point I had a look at the output during the installation process. The following configure call was made:
```
./configure --with-hpppddir=/usr/share/ppd/HP --libdir=/usr/lib --prefix=/usr --enable-qt4 --disable-qt5 --enable-doc-build --disable-cups-ppd-install --disable-foomatic-drv-install --disable-libusb01_build --disable-foomatic-ppd-install --disable-hpijs-install --disable-udev_sysfs_rules --disable-policykit --enable-cups-drv-install --enable-hpcups-install --enable-network-build --enable-dbus-build --enable-scan-build --enable-fax-build --enable-apparmor_build
```

I don't know why the option "--disable-libusb01_build" was set during the installation routine. I just gave it a try with this option enabled instead:
```
Ich@Mein-Computer:~/Downloads/hplip-3.17.10$ ./configure --with-hpppddir=/usr/share/ppd/HP --libdir=/usr/lib  --prefix=/usr --enable-qt4 --disable-qt5 --enable-doc-build  --disable-cups-ppd-install --disable-foomatic-drv-install  --enable-libusb01_build --disable-foomatic-ppd-install  --disable-hpijs-install --disable-udev_sysfs_rules --disable-policykit  --enable-cups-drv-install --enable-hpcups-install --enable-network-build  --enable-dbus-build --enable-scan-build --enable-fax-build  --enable-apparmor_build
make
make clean
sudo make install
hp-setup

```

Now hp-setup loaded just fine and prompted for the plugin download and installation during the setup routine - my shiny M277dw has returned to working as it should. Scanning with gimp/xsane and printing (both via network) are back, but I did not try out the fax. :)

I did only test the slightly changed configure call and installation with hplip-3.17.10. As I have a working system now, I won't change it.
Probably it would work with the recent hplip-3.18.3 as well. Just copy the .configure call during the first try with hplip-3.18.3.run and change the libusb01_build flag.

I hope, this helps others, as well!

---

