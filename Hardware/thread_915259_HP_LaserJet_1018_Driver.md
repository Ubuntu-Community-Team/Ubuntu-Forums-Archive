---
title: "HP LaserJet 1018 Driver"
date: 2008-09-09
forum: Hardware
---

### Post by sankscan on 2008-09-09
I'm trying to install my HP LaserJet 1018 on my ubuntu desktop and I'm looking for the right driver which I don't seem to be finding. Can anyone help me with the repos where I can get drivers along with installation instructions?

---

### Post by Sub101 on 2008-09-09
If you type

```
hp-setup
```

in terminal it should either ask you to install hplip or begin setting it up for you. HP is very well supported.

---

### Post by sankscan on 2008-09-09
> **Sub101 said:**
> If you type

```
hp-setup
```

in terminal it should either ask you to install hplip or begin setting it up for you. HP is very well supported.

Thanks Sub! I'll try that at home and let you know.

---

### Post by Sub101 on 2008-09-09
Let me know how it goes. Any more help needed please ask.

---

### Post by sankscan on 2008-09-10
> **Sub101 said:**
> Let me know how it goes. Any more help needed please ask.

Sub,

I get this message. Please advice.
**********************
root@diksha:~# hp-setup

HP Linux Imaging and Printing System (ver. 2.8.2)
Printer/Fax Setup Utility ver. 7.0

Copyright (c) 2001-7 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

No protocol specified
hp-setup: cannot connect to X server :0.0
***********************

---

### Post by Sef on 2008-09-10
> I'm trying to install my HP LaserJet 1018 on my ubuntu desktop and I'm looking for the right driver which I don't seem to be finding. Can anyone help me with the repos where I can get drivers along with installation instructions?Was your printer plugged in and turned on when you tried to print or do the set up?  It should automatically be detected.  If it hasn't for some reason, here is the HP [download]("http://hplip.sourceforge.net/downloads.html").  Use the automatic installer.

 As for a GUI, one is available from Add/Remove:  Applications > Add/Remove > Search: HPLIP > check the box next to HPLIP Toolbox > apply changes > apply > close.

---

### Post by sankscan on 2008-09-11
> **Sef said:**
> Was your printer plugged in and turned on when you tried to print or do the set up?  It should automatically be detected.  If it hasn't for some reason, here is the HP [download]("http://hplip.sourceforge.net/downloads.html").  Use the automatic installer.

 As for a GUI, one is available from Add/Remove:  Applications > Add/Remove > Search: HPLIP > check the box next to HPLIP Toolbox > apply changes > apply > close.

**************
It looks like HP-LIP is already installed but I'm still not able to print. The printer is powered on and connected via USB port to my ubuntu machine. When I print a job, I can see it in the queue and it disappears with a few seconds without the job coming out of the printer! I'm wondering what else do I do!!?

---

### Post by Sub101 on 2008-09-11
Run ```
hp-check
```

and see what output you get. 

Also i would suggest not running it as root.

---

### Post by sankscan on 2008-09-11
> **Sub101 said:**
> Run ```
hp-check
```

and see what output you get. 

Also i would suggest not running it as root.

This is what I got when I ran >hp-check
****************************************
 hp-check

HP Linux Imaging and Printing System (ver. 2.8.2)
Dependency/Version Check Utility ver. 13.0

Copyright (c) 2001-7 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

Note: hp-check can be run in three modes:
1. Compile-time check mode (-c or --compile): Use this mode before compiling the HPLIP
supplied tarball (.tar.gz or .run) to determine if the proper dependencies are        
installed to successfully compile HPLIP.                                              
2. Run-time check mode (-r or --run): Use this mode to determine if a distro supplied 
package (.deb, .rpm, etc) or an already built HPLIP supplied tarball has the proper   
dependencies installed to successfully run.                                           
3. Both compile- and run-time check mode (-b or --both) (Default): This mode will     
check both of the above cases (both compile- and run-time dependencies).              

Saving output in log file: hp-check.log

Initializing. Please wait...
warning: Invalid drv_dir value: /usr/share/cups/drv/hp/

---------------
| SYSTEM INFO |
---------------

Basic system information:
Linux diksha 2.6.24-19-generic #1 SMP Wed Aug 20 22:56:21 UTC 2008 i686 GNU/Linux

Distribution:
ubuntu 8.04

HPOJ running?
No, HPOJ is not running (OK).

Checking Python version...
OK, version 2.5.2 installed

Checking PyQt version...
OK, version 3.17 installed.

Checking SIP version...
error: SIP not installed or version not found.

Checking for CUPS...
Status: scheduler is running
error: Version: (Not available. CUPS may not be installed or not running.)


------------------------------------
| COMPILE AND RUNTIME DEPENDENCIES |
------------------------------------

note: To check for compile-time only dependencies, re-run hp-check with the -c parameter (ie, hp-check -c).
note: To check for run-time only dependencies, re-run hp-check with the -r parameter (ie, hp-check -r).

Checking for dependency: cups - Common Unix Printing System...
OK, found.

Checking for dependency: cups-ddk - CUPS driver development kit...
OK, found.

Checking for dependency: cups-devel- Common Unix Printing System development files...
error: NOT FOUND! This is a REQUIRED/COMPILE TIME ONLY dependency. Please make sure that this dependency is installed before installing or running HPLIP.
To install this dependency, execute this command:
sudo apt-get install --yes --force-yes libcupsys2-dev cupsys-bsd

Checking for dependency: gcc - GNU Project C and C++ Compiler...
error: NOT FOUND! This is a REQUIRED/COMPILE TIME ONLY dependency. Please make sure that this dependency is installed before installing or running HPLIP.
To install this dependency, execute this command:
sudo apt-get install --yes --force-yes build-essential

Checking for dependency: GhostScript - PostScript and PDF language interpreter and previewer...
OK, found.

Checking for dependency: libcrypto - OpenSSL cryptographic library...
error: NOT FOUND! This is a REQUIRED dependency. Please make sure that this dependency is installed before installing or running HPLIP.
To install this dependency, execute this command:
sudo apt-get install --yes --force-yes openssl

Checking for dependency: libjpeg - JPEG library...
error: NOT FOUND! This is a REQUIRED dependency. Please make sure that this dependency is installed before installing or running HPLIP.
To install this dependency, execute this command:
sudo apt-get install --yes --force-yes libjpeg62-dev

Checking for dependency: libnetsnmp-devel - SNMP networking library development files...
error: NOT FOUND! This is a REQUIRED dependency. Please make sure that this dependency is installed before installing or running HPLIP.
To install this dependency, execute this command:
sudo apt-get install --yes --force-yes libsnmp-dev

Checking for dependency: libpthread - POSIX threads library...
OK, found.

Checking for dependency: libtool - Library building support services...
error: NOT FOUND! This is a REQUIRED/COMPILE TIME ONLY dependency. Please make sure that this dependency is installed before installing or running HPLIP.
To install this dependency, execute this command:
sudo apt-get install --yes --force-yes libtool

Checking for dependency: libusb - USB library...
error: NOT FOUND! This is a REQUIRED dependency. Please make sure that this dependency is installed before installing or running HPLIP.
To install this dependency, execute this command:
sudo apt-get install --yes --force-yes libusb-dev

Checking for dependency: make - GNU make utility to maintain groups of programs...
OK, found.

Checking for dependency: PIL - Python Imaging Library (required for commandline scanning with hp-scan)...
OK, found.

Checking for dependency: ppdev - Parallel port support kernel module....
OK, found.

Checking for dependency: PyQt - Qt interface for Python...
OK, found.

Checking for dependency: python-devel - Python development files...
error: NOT FOUND! This is a REQUIRED/COMPILE TIME ONLY dependency. Please make sure that this dependency is installed before installing or running HPLIP.
To install this dependency, execute this command:
sudo apt-get install --yes --force-yes python2.5-dev

Checking for dependency: Python 2.3 or greater - Required for fax functionality...
OK, found.

Checking for dependency: Python 2.2 or greater - Python programming language...
OK, found.

Checking for dependency: Reportlab - PDF library for Python...
OK, found.

Checking for dependency: SANE - Scanning library...
OK, found.

Checking for dependency: SANE - Scanning library development files...
error: NOT FOUND! This is a REQUIRED/COMPILE TIME ONLY dependency. Please make sure that this dependency is installed before installing or running HPLIP.
To install this dependency, execute this command:
sudo apt-get install --yes --force-yes libsane-dev

Checking for dependency: scanimage - Shell scanning program...
OK, found.

Checking for dependency: xsane - Graphical scanner frontend for SANE...
OK, found.


----------------------
| HPLIP INSTALLATION |
----------------------


Currently installed HPLIP version...
HPLIP 2.8.2 currently installed in '/usr/share/hplip'.

Current contents of '/etc/hp/hplip.conf' file:
# hplip.conf.  Generated from hplip.conf.in by configure.

[hpssd]
# Note: hpssd does not support dynamic ports
# Port 2207 is the IANA assigned port for hpssd
port=2207

[hplip]
version=2.8.2

[dirs]
home=/usr/share/hplip
run=/var/run
ppd=/usr/share/ppd/hpijs/HP
ppdbase=/usr/share/ppd/hpijs
doc=/usr/share/doc/hplip-doc/HTML
icon=no
cupsbackend=/usr/lib/cups/backend
cupsfilter=/usr/lib/cups/filter
drv=/usr/share/cups/drv

# Following values are determined at configure time and cannot be changed.
[configure]
network-build=yes
pp-build=yes
gui-build=yes
scanner-build=yes
fax-build=yes
cups11-build=no
doc-build=yes
shadow-build=no
foomatic-drv-install=yes
foomatic-ppd-install=no
foomatic-rip-hplip-install=no
internal-tag=2.8.2.10


-------------------------------
| DISCOVERED PARALLEL DEVICES |
-------------------------------

No devices found.

--------------------------
| DISCOVERED USB DEVICES |
--------------------------

  Device URI                          Model            
  ----------------------------------  -----------------
  hp:/usb/HP_LaserJet_1018?serial=KP  HP LaserJet 1018 
  17FDZ                                                

---------------------------------
| INSTALLED CUPS PRINTER QUEUES |
---------------------------------

 
HP_LaserJet_1018
----------------
Type: Unknown
Installed in HPLIP?: No, not using the hp: or hpfax: CUPS backend.
Device URI: usb://HP/LaserJet%201018
PPD: /etc/cups/ppd/HP_LaserJet_1018.ppd
PPD Description: HP LaserJet 1018 Foomatic/foo2zjs (recommended)
Printer status: printer HP_LaserJet_1018 is idle.  enabled since Thu 11 Sep 2008 01:21:57 PM PDT
warning: Printer is not HPLIP installed. Printers must use the hp: or hpfax: CUPS backend to function in HPLIP.
PDF
---
Type: Unknown
Installed in HPLIP?: No, not using the hp: or hpfax: CUPS backend.
Device URI: cups-pdf:/
PPD: /etc/cups/ppd/PDF.ppd
PPD Description: Generic PDF file generator
Printer status: printer PDF is idle.  enabled since Sun 28 Oct 2007 09:04:11 PM PDT
warning: Printer is not HPLIP installed. Printers must use the hp: or hpfax: CUPS backend to function in HPLIP.

----------------------
| SANE CONFIGURATION |
----------------------

'hpaio' in '/etc/sane.d/dll.conf'...
error: Not found. SANE backend 'hpaio' NOT properly setup (needs to be added to /etc/sane.d/dll.conf).

Checking output of 'scanimage -L'...
 
No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).


---------------------
| PYTHON EXTENSIONS |
---------------------

Checking 'cupsext' CUPS extension...
OK, found.

Checking 'pcardext' Photocard extension...
OK, found.

Checking 'hpmudext' I/O extension...
OK, found.

Checking 'scanext' SANE scanning extension...
OK, found.


-----------------
| USB I/O SETUP |
-----------------


Checking for permissions of USB attached printers...
 
HP Device 0x4117 at 001:002: 
    Device URI: hp:/usb/HP_LaserJet_1018?serial=KP17FDZ
    Device node: /dev/bus/usb/001/002
    Mode: 0660
getfacl: Removing leading '/' from absolute path names
# file: dev/bus/usb/001/002
# owner: lp
# group: scanner
user::rw-
user:sunny:rw-
group::rw-
mask::rw-
other::---



-----------
| SUMMARY |
-----------

error: 14 errors and/or warnings.

Summary of needed commands to run to satisfy missing dependencies:
sudo apt-get install --yes --force-yes libcupsys2-dev cupsys-bsd
sudo apt-get install --yes --force-yes build-essential
sudo apt-get install --yes --force-yes openssl
sudo apt-get install --yes --force-yes libjpeg62-dev
sudo apt-get install --yes --force-yes libsnmp-dev
sudo apt-get install --yes --force-yes libtool
sudo apt-get install --yes --force-yes libusb-dev
sudo apt-get install --yes --force-yes python2.5-dev
sudo apt-get install --yes --force-yes libsane-dev

Please refer to the installation instructions at:
[http://hplip.sourceforge.net/install/index.html](http://hplip.sourceforge.net/install/index.html)
******************************************************

---

### Post by Sub101 on 2008-09-12
Install the dependencies listed at the bottom and try running hp-setup again.

Also, does this printer have wireless capacity or network connection. I have found that this type of printer is far easier to install.

---

### Post by sankscan on 2008-09-15
> **Sub101 said:**
> Install the dependencies listed at the bottom and try running hp-setup again.

Also, does this printer have wireless capacity or network connection. I have found that this type of printer is far easier to install.
****************************************
I installed all the dependencies including xsane. It is complaining that xsane is not installed. I still can't get it to work!! I listed below the outputs of;
#hp-check
#hp-setup
#sudo apt-get install --yes --force-yes xsane

I see this warning:
warning: Printer is not HPLIP installed. Printers must use the hp: or hpfax: CUPS backend to function in HPLIP.
I installed most of the dependencies for CUPS and HP. Just wondering what's required!
****************************************
root@diksha:~# hp-check

HP Linux Imaging and Printing System (ver. 2.8.2)
Dependency/Version Check Utility ver. 13.0

Copyright (c) 2001-7 Hewlett-Packard Development Company, LP
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

Saving output in log file: hp-check.log

Initializing. Please wait...
warning: Invalid drv_dir value: /usr/share/cups/drv/hp/

---------------
| SYSTEM INFO |
---------------

Basic system information:
Linux diksha 2.6.24-19-generic #1 SMP Wed Aug 20 22:56:21 UTC 2008 i686 GNU/Linux

Distribution:
ubuntu 8.04

HPOJ running?
No, HPOJ is not running (OK).

Checking Python version...
OK, version 2.5.2 installed

Checking PyQt version...
OK, version 3.17 installed.

Checking SIP version...
error: SIP not installed or version not found.

Checking for CUPS...
Status: scheduler is running
Version: 1.3.7


------------------------------------
| COMPILE AND RUNTIME DEPENDENCIES |
------------------------------------

note: To check for compile-time only dependencies, re-run hp-check with the -c parameter (ie, hp-check -c).
note: To check for run-time only dependencies, re-run hp-check with the -r parameter (ie, hp-check -r).

Checking for dependency: cups - Common Unix Printing System...
OK, found.

Checking for dependency: cups-ddk - CUPS driver development kit...
OK, found.

Checking for dependency: cups-devel- Common Unix Printing System development files...
OK, found.

Checking for dependency: gcc - GNU Project C and C++ Compiler...
OK, found.

Checking for dependency: GhostScript - PostScript and PDF language interpreter and previewer...
OK, found.

Checking for dependency: libcrypto - OpenSSL cryptographic library...
OK, found.

Checking for dependency: libjpeg - JPEG library...
OK, found.

Checking for dependency: libnetsnmp-devel - SNMP networking library development files...
OK, found.

Checking for dependency: libpthread - POSIX threads library...
OK, found.

Checking for dependency: libtool - Library building support services...
OK, found.

Checking for dependency: libusb - USB library...
OK, found.

Checking for dependency: make - GNU make utility to maintain groups of programs...
OK, found.

Checking for dependency: PIL - Python Imaging Library (required for commandline scanning with hp-scan)...
OK, found.

Checking for dependency: ppdev - Parallel port support kernel module....
OK, found.

Checking for dependency: PyQt - Qt interface for Python...
OK, found.

Checking for dependency: python-devel - Python development files...
OK, found.

Checking for dependency: Python 2.3 or greater - Required for fax functionality...
OK, found.

Checking for dependency: Python 2.2 or greater - Python programming language...
OK, found.

Checking for dependency: Reportlab - PDF library for Python...
OK, found.

Checking for dependency: SANE - Scanning library...
OK, found.

Checking for dependency: SANE - Scanning library development files...
OK, found.

Checking for dependency: scanimage - Shell scanning program...
OK, found.

Checking for dependency: xsane - Graphical scanner frontend for SANE...
warning: NOT FOUND! This is an OPTIONAL/RUNTIME ONLY dependency. Some HPLIP functionality may not function properly.
To install this dependency, execute this command:
sudo apt-get install --yes --force-yes xsane


----------------------
| HPLIP INSTALLATION |
----------------------


Currently installed HPLIP version...
HPLIP 2.8.2 currently installed in '/usr/share/hplip'.

Current contents of '/etc/hp/hplip.conf' file:
# hplip.conf.  Generated from hplip.conf.in by configure.

[hpssd]
# Note: hpssd does not support dynamic ports
# Port 2207 is the IANA assigned port for hpssd
port=2207

[hplip]
version=2.8.2

[dirs]
home=/usr/share/hplip
run=/var/run
ppd=/usr/share/ppd/hpijs/HP
ppdbase=/usr/share/ppd/hpijs
doc=/usr/share/doc/hplip-doc/HTML
icon=no
cupsbackend=/usr/lib/cups/backend
cupsfilter=/usr/lib/cups/filter
drv=/usr/share/cups/drv

# Following values are determined at configure time and cannot be changed.
[configure]
network-build=yes
pp-build=yes
gui-build=yes
scanner-build=yes
fax-build=yes
cups11-build=no
doc-build=yes
shadow-build=no
foomatic-drv-install=yes
foomatic-ppd-install=no
foomatic-rip-hplip-install=no
internal-tag=2.8.2.10


-------------------------------
| DISCOVERED PARALLEL DEVICES |
-------------------------------

No devices found.

--------------------------
| DISCOVERED USB DEVICES |
--------------------------

  Device URI                        Model           
  --------------------------------  ----------------
  hp:/usb/HP_LaserJet_1018?serial=  HP LaserJet 1018
  KP17FDZ                                           

---------------------------------
| INSTALLED CUPS PRINTER QUEUES |
---------------------------------

 
HP_LaserJet_1018
----------------
Type: Unknown
Installed in HPLIP?: No, not using the hp: or hpfax: CUPS backend.
Device URI: usb://HP/LaserJet%201018
PPD: /etc/cups/ppd/HP_LaserJet_1018.ppd
PPD Description: HP LaserJet 1018 Foomatic/foo2zjs (recommended)
Printer status: printer HP_LaserJet_1018 is idle.  enabled since Sun 14 Sep 2008 09:15:28 PM PDT
warning: Printer is not HPLIP installed. Printers must use the hp: or hpfax: CUPS backend to function in HPLIP.
PDF
---
Type: Unknown
Installed in HPLIP?: No, not using the hp: or hpfax: CUPS backend.
Device URI: cups-pdf:/
PPD: /etc/cups/ppd/PDF.ppd
PPD Description: Generic PDF file generator
Printer status: printer PDF is idle.  enabled since Sun 28 Oct 2007 09:04:11 PM PDT
warning: Printer is not HPLIP installed. Printers must use the hp: or hpfax: CUPS backend to function in HPLIP.

----------------------
| SANE CONFIGURATION |
----------------------

'hpaio' in '/etc/sane.d/dll.conf'...
OK, found. SANE backend 'hpaio' is properly set up.

Checking output of 'scanimage -L'...
 
No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).


---------------------
| PYTHON EXTENSIONS |
---------------------

Checking 'cupsext' CUPS extension...
OK, found.

Checking 'pcardext' Photocard extension...
OK, found.

Checking 'hpmudext' I/O extension...
OK, found.

Checking 'scanext' SANE scanning extension...
OK, found.


-----------------
| USB I/O SETUP |
-----------------


Checking for permissions of USB attached printers...
 
HP Device 0x4117 at 001:002: 
    Device URI: hp:/usb/HP_LaserJet_1018?serial=KP17FDZ
    Device node: /dev/bus/usb/001/002
    Mode: 0660
getfacl: Removing leading '/' from absolute path names
# file: dev/bus/usb/001/002
# owner: lp
# group: scanner
user::rw-
user:sunny:rw-
group::rw-
mask::rw-
other::---



-----------
| SUMMARY |
-----------

error: 4 errors and/or warnings.

Summary of needed commands to run to satisfy missing dependencies:
sudo apt-get install --yes --force-yes xsane

Please refer to the installation instructions at:
[http://hplip.sourceforge.net/install/index.html](http://hplip.sourceforge.net/install/index.html)
**************************************************
root@diksha:~# hp-setup

HP Linux Imaging and Printing System (ver. 2.8.2)
Printer/Fax Setup Utility ver. 7.0

Copyright (c) 2001-7 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

No protocol specified
hp-setup: cannot connect to X server :0.0
***************************************************
root@diksha:~# sudo apt-get install --yes --force-yes xsane
Reading package lists... Done
Building dependency tree       
Reading state information... Done
xsane is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
****************************************************

---

### Post by sankscan on 2008-09-15
No my printer is not network or wireless ready....:(

---

### Post by sankscan on 2008-09-24
> **sankscan said:**
> No my printer is not network or wireless ready....:(

Do you think HP LaserJet 1018 is incompatible with Ubuntu Desktop? Anybody?

---

### Post by Sub101 on 2008-09-24
Sorry about the long time for reply. Well to be honest i would have thought it would work as HP does tend to however i do not know for certain.

  Is HPLIP still causing problems?

---

### Post by sub2007 on 2008-09-24
> **sankscan said:**
> Do you think HP LaserJet 1018 is incompatible with Ubuntu Desktop? Anybody?

It does work with Ubuntu. I wrote this unofficial guide (it basically uses the official guide but tailored for Ubuntu) a while back which seems to have worked with reasonable success:

[http://ubuntuforums.org/showpost.php?p=4888291&postcount=9](http://ubuntuforums.org/showpost.php?p=4888291&postcount=9)

---

### Post by sankscan on 2008-10-02
> **sub2007 said:**
> It does work with Ubuntu. I wrote this unofficial guide (it basically uses the official guide but tailored for Ubuntu) a while back which seems to have worked with reasonable success:

[http://ubuntuforums.org/showpost.php?p=4888291&postcount=9](http://ubuntuforums.org/showpost.php?p=4888291&postcount=9)

Sub,

I'll try what you suggested and see if it should work. If it doesn't I'll plainly give up! Any clue how to get my wireless PCI card to come to life? It's a D-Link b/g card. I don't know the exact model # but I'm assuming its drivers should be included in the latest ubuntu dtp version. Let me try to get the printer roaring first :)

Thanks,
S

---

### Post by sonu 1807 on 2008-10-03
I have exactly the same printer and I am using it . There may be better ways of doing it but I simply followed the steps given here-:[http://hplipopensource.com/hplip-web/install/manual/distros/ubuntu.html](http://hplipopensource.com/hplip-web/install/manual/distros/ubuntu.html). I am sure it would work for you. Only one thing in place of 2.8.8.44 everywhere type (or paste) 2.8.9. I am sure it would work for you as it did for me.

---

### Post by oldsoundguy on 2008-10-03
sometimes using Google will get you the answer  (actually using Google will get the answer MOST of the time:
[http://hplipopensource.com/hplip-web/models/laserjet/hp_laserjet_1018.html](http://hplipopensource.com/hplip-web/models/laserjet/hp_laserjet_1018.html)

---

### Post by ceixeoida on 2008-10-20
> **Sub101 said:**
> If you type

```
hp-setup
```

in terminal it should either ask you to install hplip or begin setting it up for you. HP is very well supported.

It worked great for me. Thanks Sub!

---

