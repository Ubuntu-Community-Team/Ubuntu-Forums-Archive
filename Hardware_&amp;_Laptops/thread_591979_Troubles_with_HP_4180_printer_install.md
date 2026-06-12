---
title: "Troubles with HP 4180 printer install"
date: 2007-10-25
forum: Hardware &amp; Laptops
---

### Post by eheyl on 2007-10-25
Hey guys!

I've got the hplip tool downloaded from the hp.com site. I bought this printer specifically because it said it was compatible with ubuntu (I'm running 7.10). Here is the log file from my install attempts. the hplip is in my /home/user directory as they suggested. I tried with synaptic to install some of the dependencies but that won't work right either...VERY frustrated...I could use some advice:

erik@hal:~$ sh hplip-2.7.10.run
Creating directory hplip-2.7.10
Verifying archive integrity... All good.
Uncompressing HPLIP 2.7.10 Self Extracting Archivecd: 353: can't cd to hplip-2.7.10
.....................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................cd: 353: can't cd to hplip-2.7.10
chown: `./hplip-2.7.10': Permission denied
chgrp: `./hplip-2.7.10': Permission denied

cd: 356: can't cd to hplip-2.7.10

HP Linux Imaging and Printing System (ver. 2.7.10)
HPLIP Installer ver. 3.0

Copyright (c) 2001-7 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

Installer log saved in: hplip-install_Thu-25-Oct-2007_23:19:34.log

Initializing. Please wait...
 
note: Defaults for each question are maked with a '*'. Press <enter> to accept the default.


INSTALLATION MODE
-----------------
Automatic mode will install the full HPLIP solution with the most common options.
Custom mode allows you to chose installation options to fit specific requirements.

Please choose the installation mode (a=automatic*, c=custom, q=quit) : a


INTRODUCTION
------------
This installer will install HPLIP version 2.7.10 on your computer.
Please close any running package management systems now (YaST, Adept, Synaptic, Up2date, etc).


DISTRO/OS CONFIRMATION
----------------------
Distro appears to be Ubuntu 7.10.

Is "Ubuntu 7.10" your correct distro/OS and version (y=yes*, n=no, q=quit) ? y


ENTER ROOT/SUPERUSER PASSWORD
-----------------------------
Please enter the root/superuser password: 
Password accepted


INSTALLATION NOTES
------------------
Enable the universe/multiverse repositories. See: [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu) for more information.  Disable the CD-ROM/DVD source if you do not have the Ubunbtu installation media inserted in the drive.

Please read the installation notes. Press <enter> to continue or 'q' to quit: 


RUNNING PRE-INSTALL COMMANDS
----------------------------


INSTALL MISSING REQUIRED DEPENDENCIES
-------------------------------------
warning: There are 7 missing REQUIRED dependencies.
note: Installation of dependencies requires an active internet connection.
warning: Missing REQUIRED dependency: gcc (gcc - GNU Project C and C++ Compiler)
warning: Missing REQUIRED dependency: libpthread (libpthread - POSIX threads library)
warning: Missing REQUIRED dependency: python-devel (python-devel - Python development files)
warning: Missing REQUIRED dependency: cups-devel (cups-devel- Common Unix Printing System development files)
warning: Missing REQUIRED dependency: libusb (libusb - USB library)
warning: Missing REQUIRED dependency: libtool (libtool - Library building support services)
warning: Missing REQUIRED dependency: libjpeg (libjpeg - JPEG library)


INSTALL MISSING OPTIONAL DEPENDENCIES
-------------------------------------
warning: There are 7 missing OPTIONAL dependencies.
note: Installation of dependencies requires an active internet connection.
warning: Missing REQUIRED dependency for option 'network': libcrypto (libcrypto - OpenSSL cryptographic library)
warning: Missing REQUIRED dependency for option 'network': libnetsnmp-devel (libnetsnmp-devel - SNMP networking library development files)
warning: Missing REQUIRED dependency for option 'gui': pyqt (PyQt - Qt interface for Python)
warning: Missing OPTIONAL dependency for option 'fax': reportlab (Reportlab - PDF library for Python)
warning: Missing REQUIRED dependency for option 'scan': sane-devel (SANE - Scanning library development files)
warning: Missing OPTIONAL dependency for option 'scan': pil (PIL - Python Imaging Library (required for commandline scanning with hp-scan))
warning: Missing OPTIONAL dependency for option 'scan': scanimage (scanimage - Shell scanning program)


CHECKING FOR NETWORK CONNECTION
-------------------------------
Network connection present.


RUNNING PRE-PACKAGE COMMANDS
----------------------------
sudo dpkg --configure -a (Pre-depend step 1)
sudo apt-get install --yes --force-yes -f (Pre-depend step 2)
sudo apt-get update (Pre-depend step 3)


DEPENDENCY AND CONFLICT RESOLUTION
----------------------------------
Running 'sudo apt-get install --yes --force-yes build-essential build-essential python2.5-dev libcupsys2-dev cupsys-bsd libusb-dev libtool libjpeg62-dev openssl libsnmp9-dev python-qt3 python-reportlab libsane-dev python-imaging libsane'
Please wait, this may take several minutes...
error: Package install command failed with error code 100
Would you like to retry installing the missing package(s) (y=yes*, n=no, q=quit) ? y
Running 'sudo apt-get install --yes --force-yes build-essential build-essential python2.5-dev libcupsys2-dev cupsys-bsd libusb-dev libtool libjpeg62-dev openssl libsnmp9-dev python-qt3 python-reportlab libsane-dev python-imaging libsane'
Please wait, this may take several minutes...
error: Package install command failed with error code 100
Would you like to retry installing the missing package(s) (y=yes*, n=no, q=quit) ? n
warning: Some HPLIP functionality might not function due to missing package(s).
error: A required dependency 'gcc (gcc - GNU Project C and C++ Compiler)' is still missing.
error: A required dependency 'libpthread (libpthread - POSIX threads library)' is still missing.
error: A required dependency 'python-devel (python-devel - Python development files)' is still missing.
error: A required dependency 'cups-devel (cups-devel- Common Unix Printing System development files)' is still missing.
error: A required dependency 'libusb (libusb - USB library)' is still missing.
error: A required dependency 'libtool (libtool - Library building support services)' is still missing.
error: A required dependency 'libjpeg (libjpeg - JPEG library)' is still missing.
error: Installation cannot continue without these dependencies.
error: Please manually install this dependency and re-run this installer.


A couple of things jump out at me: it wants me to enable universe/multiverse repositories and I'm not sure how to do that in gutsy as the page only gives info for fiesty (that and I think I'd need a walkthrough) and what the heck is error code 100??? and its the HP F4180 multifunction.

---

### Post by eheyl on 2007-10-26
*bump* Anyone?

---

### Post by eheyl on 2007-10-26
It prints fine (just in ubuntu without the hp tool) and seems to copy too, but I'd really like to get the scan working. and I think I need the hp tool for that. Anyone have experience with this?

---

### Post by eheyl on 2007-10-26
How can I get the missing dependencies?

---

### Post by eheyl on 2007-10-26
Found another thread with the exact issue (though couldn't find it via search) and everything is fine now! YA!

---

### Post by Quid on 2008-05-25
Take a look at this link - It shows the link to review repositories that are required to check the dependancies... It worked for me - I needed to enable Multiverse and reset to the Main repos.
[http://ubuntuforums.org/showthread.php?t=184838](http://ubuntuforums.org/showthread.php?t=184838)

---

