---
title: "Issue installing HP DeskJet 3630 drivers on Ubuntu 18.04"
date: 2018-05-31
forum: Hardware
---

### Post by Drone4four on 2018-05-31
I can&#8217;t get my **HP DeskJet 3630** printer software to run on Ubuntu 18.04.  I bought the hardware in summer 2016 and have installed the drivers on previous Ubuntu releases no problem.

I installed the drivers and utilities from the official Ubuntu package repo rather than running the install scripts from HP&#8217;s website.

After installing, when I go to run the utility, here is the small traceback I get:
```
$ hp-setup                       
HP Linux Imaging and Printing System (ver. 3.17.10)
Printer/Fax Setup Utility ver. 9.0

Copyright (c) 2001-15 HP Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

error: libQt5Widgets.so.5: cannot open shared object file: No such file or directory
$ hp-info 
HP Linux Imaging and Printing System (ver. 3.17.10)
Device Information Utility ver. 5.2

Copyright (c) 2001-15 HP Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

error: libQt5Widgets.so.5: cannot open shared object file: No such file or directory
$
```

When I Googled 'libQt5Widgets.so.5: cannot open shared object file: No such file or directory', it turned up users encountering a similar issue from 2016 but [trying to run an Android emulator]("https://github.com/bitrise-io/build.issues/issues/39").  Not really applicable, right?

Here is the full output of $ hp-check:
```
[01mSaving output in log file: /home/gnull/hp-check.log[0m

[01mHP Linux Imaging and Printing System (ver. 3.17.10)[0m
[01mDependency/Version Check Utility ver. 15.1[0m

Copyright (c) 2001-15 HP Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

[01mNote: hp-check can be run in three modes:[0m
1. Compile-time check mode (-c or --compile): Use this mode before compiling the HPLIP supplied tarball (.tar.gz or .run) to determine if the proper dependencies are installed to successfully compile HPLIP.                                                                       
2. Run-time check mode (-r or --run): Use this mode to determine if a distro supplied package (.deb, .rpm, etc) or an already built HPLIP supplied tarball has the proper dependencies installed to successfully run.                                                                
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


---------------
| SYSTEM INFO |
---------------

 Kernel: 4.15.0-22-generic #24-Ubuntu SMP Wed May 16 12:15:17 UTC 2018 GNU/Linux
 Host: gnosis
 Proc: 4.15.0-22-generic #24-Ubuntu SMP Wed May 16 12:15:17 UTC 2018 GNU/Linux
 Distribution: 12 18.04
 Bitness: 64 bit


-----------------------
| HPLIP CONFIGURATION |
-----------------------

HPLIP-Version: HPLIP 3.17.10
HPLIP-Home: /usr/share/hplip

[01mCurrent contents of '/etc/hp/hplip.conf' file:[0m
# hplip.conf.  Generated from hplip.conf.in by configure.

[hplip]
version=3.17.10

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
internal-tag=3.17.10
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


[01mCurrent contents of '/var/lib/hp/hplip.state' file:[0m
Plugins are not installed. Could not access file: No such file or directory

[01mCurrent contents of '~/.hplip/hplip.conf' file:[0m
[commands]
scan = /usr/bin/xsane -V %SANE_URI%

[fax]
email_address = 
voice_phone = 

[installation]
date_time = 05/31/18 10:36:41
version = 3.17.10

[last_used]
device_uri = hp:/usb/DeskJet_3630_series?serial=CN66H3H1VD067P
printer_name = DeskJet_3630
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
last_upgraded_time = 1490051144
latest_available_version = 3.16.11
notify_upgrade = true
pending_upgrade_time = 0


 <Package-name>        <Package-Desc>      <Required/Optional> <Min-Version> <Installed-Version> <Status>   <Comment>

-------------------------
| External Dependencies |
-------------------------

 cups                 CUPS - Common Unix Printing System                           REQUIRED        1.1             2.2.7           OK         'CUPS Scheduler is running'
 gs                   GhostScript - PostScript and PDF language interpreter and previewer REQUIRED        7.05            9.22            OK         -
 xsane                xsane - Graphical scanner frontend for SANE                  OPTIONAL        0.9             0.999           OK         -
 scanimage            scanimage - Shell scanning program                           OPTIONAL        1.0             1.0.27          OK         -
 dbus                 DBus - Message bus system                                    REQUIRED        -               1.12.2          OK         -
 policykit            PolicyKit - Administrative policy framework                  OPTIONAL        -               0.105           OK         -
 network              network -wget                                                OPTIONAL        -               1.19.4          OK         -
 avahi-utils          avahi-utils                                                  OPTIONAL        -               0.7             OK         -

------------------------
| General Dependencies |
------------------------

 libjpeg              libjpeg - JPEG library                                       REQUIRED        -               -               OK         -
 cups-devel           CUPS devel- Common Unix Printing System development files    REQUIRED        -               2.2.7           OK         -
 cups-image           CUPS image - CUPS image development files                    REQUIRED        -               2.2.7           OK         -
 libpthread           libpthread - POSIX threads library                           REQUIRED        -               b'2.27'         OK         -
 libusb               libusb - USB library                                         REQUIRED        -               1.0             OK         -
 sane                 SANE - Scanning library                                      REQUIRED        -               -               OK         -
 sane-devel           SANE - Scanning library development files                    REQUIRED        -               -               OK         -
 libnetsnmp-devel     libnetsnmp-devel - SNMP networking library development files REQUIRED        5.0.9           5.7.3           OK         -
 libcrypto            libcrypto - OpenSSL cryptographic library                    REQUIRED        -               1.1.0           OK         -
 python3X             Python 2.2 or greater - Python programming language          REQUIRED        2.2             3.6.5           OK         -
 python3-notify2      Python libnotify - Python bindings for the libnotify Desktop notifications OPTIONAL        -               -               OK         -
 python3-pyqt4-dbus   PyQt 4 DBus - DBus Support for PyQt4                         OPTIONAL        4.0             4.12.1          OK         -
 python3-pyqt4        PyQt 4- Qt interface for Python (for Qt version 4.x)         REQUIRED        4.0             4.12.1          OK         -
 python3-dbus         Python DBus - Python bindings for DBus                       REQUIRED        0.80.0          1.2.6           OK         -
 python3-xml          Python XML libraries                                         REQUIRED        -               2.2.5           OK         -
 python3-devel        Python devel - Python development files                      REQUIRED        2.2             3.6.5           OK         -
 python3-pil          PIL - Python Imaging Library (required for commandline scanning with hp-scan) OPTIONAL        -               1.1.7           OK         -
 python3-reportlab    Reportlab - PDF library for Python                           OPTIONAL        2.0             3.4.0           OK         -

--------------
| COMPILEDEP |
--------------

 libtool              libtool - Library building support services                  REQUIRED        -               2.4.6           OK         -
 gcc                  gcc - GNU Project C and C++ Compiler                         REQUIRED        -               7.3.0           OK         -
 make                 make - GNU make utility to maintain groups of programs       REQUIRED        3.0             4.1             OK         -

---------------------
| Python Extentions |
---------------------

 cupsext              CUPS-Extension                                               REQUIRED        -               3.17.10         OK         -
 hpmudext             IO-Extension                                                 REQUIRED        -               3.17.10         OK         -

----------------------
| Scan Configuration |
----------------------

'/etc/sane.d/dll.d/hpaio' not found.
 hpaio                HPLIP-SANE-Backend                                           REQUIRED        -               3.17.10         OK         'hpaio found in /etc/sane.d/dll.conf'
 scanext              Scan-SANE-Extension                                          REQUIRED        -               3.17.10         OK         -

------------------------------
| DISCOVERED SCANNER DEVICES |
------------------------------

device `hpaio:/usb/DeskJet_3630_series?serial=CN66H3H1VD067P' is a Hewlett-Packard DeskJet_3630_series all-in-one


--------------------------
| DISCOVERED USB DEVICES |
--------------------------

  Device URI                                               Model                                                  
  -------------------------------------------------------  -------------------------------------------------------
  hp:/usb/DeskJet_3630_series?serial=CN66H3H1VD067P        HP DeskJet 3630 series                                 

---------------------------------
| INSTALLED CUPS PRINTER QUEUES |
---------------------------------


[01mDeskJet-3630-series[0m
[01m-------------------[0m
Type: Printer
Device URI: hp:/usb/DeskJet_3630_series?serial=CN66H3H1VD067P
PPD: /etc/cups/ppd/DeskJet-3630-series.ppd
PPD Description: 
Printer status: printer DeskJet-3630-series is idle.  enabled since Thu 26 Apr 2018 09:21:56 PM EDT
Communication status: Good


--------------
| PERMISSION |
--------------

USB             DeskJet-3630-series            Required        -        -        OK       Node:'/dev/bus/usb/003/004' Perm:'  root  lp rw- rw- rw- rw- r--'
[32;01mNo errors or warnings.[0m

Done.

```
From that output, here are some of the highlights:
```

Gtk-Message: 10:36:40.467: Failed to load module "canberra-gtk-module"
warning: 12-18.04 version is not supported. Using 12-17.04 versions dependencies to verify and install...
warning: HPLIP-Installation: Auto installation is not supported for 12 distro  18.04 version 
Gtk-Message: 10:36:42.622: Failed to load module "canberra-gtk-module"
Gtk-Message: 10:36:42.665: Failed to load module "canberra-gtk-module"
warning: Failed to read /etc/cups/ppd/DeskJet-3630-series.ppd ppd file

```

How do I successfully run hp-setup?

Is there any other information I can provide?

---

### Post by Yellow Pasque on 2018-05-31
Have you installed hplip-gui? It should get rid of the Qt5Widget error and make things easier for you. Also, I think hp-setup needs sudo/root privs.

---

### Post by Drone4four on 2018-05-31
hplip-gui was already installed:
```
$ sudo apt install hplip-gui 
[sudo] password for gnull: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
hplip-gui is already the newest version (3.17.10+repack0-5).
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

Here is hp-setup invoked as sudo:```
$ sudo hp-setup

HP Linux Imaging and Printing System (ver. 3.17.10)
Printer/Fax Setup Utility ver. 9.0

Copyright (c) 2001-15 HP Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

error: libQt5Widgets.so.5: cannot open shared object file: No such file or directory
$ 
```

Is there anything else we can try?

---

### Post by Yellow Pasque on 2018-06-01
Something else to try:
```
sudo apt-get install libqt5widgets5
```

---

### Post by Drone4four on 2018-06-01
```
$ sudo apt-get install libqt5widgets5
[sudo] password for gnull: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libqt5widgets5 is already the newest version (5.9.5+dfsg-0ubuntu1).
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
 $
```

---

### Post by Drone4four on 2018-06-07
Anyone else care to comment?

---

### Post by #&amp;thj^% on 2018-06-07
Just a thought but "sometimes" for helping others the drivers from HP help.
Version: 3.18.5 is now available from [https://developers.hp.com/hp-linux-imaging-and-printing/gethplip](https://developers.hp.com/hp-linux-imaging-and-printing/gethplip)
And verify that libqt5widgets5 is in fact installed properly
```
dpkg -l | grep libqt5widgets5
```
I'm using HP Device Manager (hplip)  3.18.4-2 now on Arch.

---

### Post by Drone4four on 2018-06-07
Is libqt5widgets5 installed correctly?
```
$ dpkg -l | grep libqt5widgets5
ii  libqt5widgets5:amd64                            5.9.5+dfsg-0ubuntu1                     amd64        Qt 5 widgets module
```

---

### Post by #&amp;thj^% on 2018-06-07
Yes it is, you can tell by seeing the leading "ii"  first one install second one installed. Hope that helps. :)
```
First letter -> desired package state ("selection state"):

    u ... unknown
    i ... install
    r ... remove/deinstall
    p ... purge (remove including config files)
    h ... hold

Second letter -> current package state:

    n ... not-installed
    i ... installed
    c ... config-files (only the config files are installed)
    U ... unpacked
    F ... half-configured (configuration failed for some reason)
    h ... half-installed (installation failed for some reason)
    W ... triggers-awaited (package is waiting for a trigger from another package)
    t ... triggers-pending (package has been triggered)

```

---

### Post by Drone4four on 2018-06-07
> **1fallen said:**
> Just a thought but "sometimes" for helping others the drivers from HP help.
Version: 3.18.5 is now available from [https://developers.hp.com/hp-linux-imaging-and-printing/gethplip](https://developers.hp.com/hp-linux-imaging-and-printing/gethplip)
I'm using HP Device Manager (hplip)  3.18.4-2 now on Arch.

That was easier than I thought.  I purged my system of the hplip packages installed from the Ubuntu repos.  I then ran the script from HP's website that you shared. The script finished and prompted me to reboot.  Now my HP Device Manager runs and I am able to print. Thank you, **@1fallen**, for your advice. 

The reason why I hesitated to run the script from HP's website is because [it was suggested to me previously that I shouldn't]("https://ubuntuforums.org/showthread.php?t=2366999"). Ah well. It's working now. Thanks again.

---

### Post by #&amp;thj^% on 2018-06-07
Yes it is a good _practice _to stay within the provided software given to use >> but at times we need to get a bit adventurous to get what we need> :D
Glad it worked and Happy Printing! ;)

---

### Post by oldfred on 2018-06-08
I used to install the hp print drivers from HP.
But when I installed 18.04, it immediately found my HP printer & set it up.

But with 18.04 there is a major change to printing.

[https://wiki.ubuntu.com/BionicBeaver/ReleaseNotes](https://wiki.ubuntu.com/BionicBeaver/ReleaseNotes)
Driverless printing support is now available. 

It uses ppd files to print which is what Mac have used for years, so most printers support ppd files.
it should show in System Settings, Devices, printers

---

