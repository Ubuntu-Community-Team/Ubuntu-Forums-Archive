---
title: "HP OfficeJet 4650 printer not working-how to fix ?"
date: 2016-05-26
forum: Hardware
---

### Post by Sid_Smith on 2016-05-26
It is connected via USB. I downloaded the script to install HPLIP printer drivers. But it gets stuck at one step which is at the bottom of the post **sudo dpkg --configure -a (Pre-depend step 1)**. Please advise how to fix this. Thanks.

**Output:**
```
john@john-pc:~/Downloads$ ./hplip-3.16.5.run 
Creating directory hplip-3.16.5
Verifying archive integrity... All good.
Uncompressing HPLIP 3.16.5 Self Extracting Archive....more dots

HP Linux Imaging and Printing System (ver. 3.16.5)
HPLIP Installer ver. 5.1


Copyright (c) 2001-15 HP Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.


Installer log saved in: hplip-install_Wed-25-May-2016_23:28:25.log


/
note: Defaults for each question are maked with a '*'. Press <enter> to accept the default.
 


INSTALLATION MODE
-----------------
Automatic mode will install the full HPLIP solution with the most common options.
Custom mode allows you to choose installation options to fit specific requirements.


Please choose the installation mode (a=automatic*, c=custom, q=quit) : a


Initializing. Please wait...




INTRODUCTION
------------
This installer will install HPLIP version 3.16.5 on your computer.
Please close any running package management systems now (YaST, Adept, Synaptic, Up2date, etc).




DISTRO/OS CONFIRMATION
----------------------
Distro appears to be Ubuntu 14.04.


Is "Ubuntu 14.04" your correct distro/OS and version (y=yes*, n=no, q=quit) ? y




ENTER USER PASSWORD
-------------------
Please enter the sudoer (john)'s password: 
 


INSTALLATION NOTES
------------------
Enable the universe/multiverse repositories. Also be sure you are using the Ubuntu "Main" Repositories. See: [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu) for more information.  Disable the CD-ROM/DVD source if you do not have the Ubuntu installation media inserted in the drive.

Please read the installation notes. Press <enter> to continue or 'q' to quit: 




SECURITY PACKAGES
-----------------
AppArmor is installed. 
AppArmor protects the application from external intrusion attempts making the application secure


Would you like to have this installer install the hplip specific policy/profile (y=yes, n=no*, q=quit) ? y




RUNNING PRE-INSTALL COMMANDS
----------------------------
OK




MISSING DEPENDENCIES
--------------------
Following dependencies are not installed. HPLIP will not work if all REQUIRED dependencies are not installed and some of the HPLIP features will not work if OPTIONAL dependencies are not installed.
Package-Name         Component            Required/Optional   
libcrypto            network              REQUIRED            
libnetsnmp-devel     network              REQUIRED            
sane-devel           scan                 REQUIRED            
gcc                  base                 REQUIRED            
python-devel         base                 REQUIRED            
cups-devel           base                 REQUIRED            
libusb               base                 REQUIRED            
libtool              base                 REQUIRED            
cups-image           base                 REQUIRED            
xsane                scan                 OPTIONAL            
libjpeg              base                 REQUIRED            
dbus                 fax                  REQUIRED            
Do you want to install these missing dependencies (y=yes*, n=no, q=quit) ? y

INSTALL MISSING REQUIRED DEPENDENCIES
-------------------------------------
note: Installation of dependencies requires an active internet connection.
warning: Missing REQUIRED dependency: gcc (gcc - GNU Project C and C++ Compiler)
warning: Missing REQUIRED dependency: python-devel (Python devel - Python development files)
warning: Missing REQUIRED dependency: cups-devel (CUPS devel- Common Unix Printing System development files)
warning: Missing REQUIRED dependency: libusb (libusb - USB library)
warning: Missing REQUIRED dependency: libtool (libtool - Library building support services)
warning: Missing REQUIRED dependency: cups-image (CUPS image - CUPS image development files)
warning: Missing REQUIRED dependency: libjpeg (libjpeg - JPEG library)
warning: Missing REQUIRED dependency: libcrypto (libcrypto - OpenSSL cryptographic library)
warning: Missing REQUIRED dependency: libnetsnmp-devel (libnetsnmp-devel - SNMP networking library development files)
warning: Missing REQUIRED dependency: dbus (DBus - Message bus system)
warning: Missing REQUIRED dependency: sane-devel (SANE - Scanning library development files)




INSTALL MISSING OPTIONAL DEPENDENCIES
-------------------------------------
note: Installation of dependencies requires an active internet connection.
warning: Missing OPTIONAL dependency for option 'scan': xsane (xsane - Graphical scanner frontend for SANE)
A package manager '/usr/bin/dpkg --status-fd' appears to be running. Please quit the package manager and press enter to continue (i=ignore, r=retry*, f=force, q=quit) :f


Force quit of package manager '/usr/bin/dpkg --status-fd' (y=yes*, n=no, q=quit) ? y
 


CHECKING FOR NETWORK CONNECTION
-------------------------------
Network connection present.




RUNNING PRE-PACKAGE COMMANDS
----------------------------
**sudo dpkg --configure -a (Pre-depend step 1)**
```

---

### Post by ajgreeny on 2016-05-26
Please use **Code-Tags** for terminal output in future. See my signature below for a **How-to**

Are you sure you have the following situation and repos enabled?
> INSTALLATION NOTES
------------------
Enable the universe/multiverse repositories. Also be sure you are using the Ubuntu "Main" Repositories. See: [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu) for more information.  Disable the CD-ROM/DVD source if you do not have the Ubuntu installation media inserted in the drive.

Please read the installation notes. Press <enter> to continue or 'q' to quit: 
Also the following warning appears which means the installation can not proceed.  Make sure any applications such as the update-manager, synaptic or software-centre are not running. Reboot if necessary and try the HPLIP installation again.
> A package manager '/usr/bin/dpkg --status-fd' appears to be running. Please quit the package manager and press enter to continue (i=ignore, r=retry*, f=force, q=quit) :f

---

### Post by vasa1 on 2016-05-26
> **Sid_Smith said:**
> ... I downloaded the script to install HPLIP printer drivers. ...

**Output:**
```
john@john-pc:~/Downloads$ ./hplip-3.16.5.run 
...

```...
Where was this script downloaded from? Why did you not just install the hplip package from the software center? The other thing is that 16.04 has version 3.16.3 and you're trying to install v3.16.5 on 14.0_4_?

It's been a while since I installed *hplip*, but, to my mind, your procedure seems far more complicated :(


```
04:17 PM .../log/apt $ zgrep hplip history.log*
history.log.10.gz:Upgrade: hplip:amd64 (3.14.3-0ubuntu3.2, 3.14.3-0ubuntu3.4), libsane-hpaio:amd64 (3.14.3-0ubuntu3.2, 3.14.3-0ubuntu3.4), libhpmud0:amd64 (3.14.3-0ubuntu3.2, 3.14.3-0ubuntu3.4), libgs9-common:amd64 (9.10~dfsg-0ubuntu10.3, 9.10~dfsg-0ubuntu10.4), printer-driver-postscript-hp:amd64 (3.14.3-0ubuntu3.2, 3.14.3-0ubuntu3.4), sqlite3:amd64 (3.8.2-1ubuntu2, 3.8.2-1ubuntu2.1), ghostscript-x:amd64 (9.10~dfsg-0ubuntu10.3, 9.10~dfsg-0ubuntu10.4), libsqlite3-0:amd64 (3.8.2-1ubuntu2, 3.8.2-1ubuntu2.1), printer-driver-hpcups:amd64 (3.14.3-0ubuntu3.2, 3.14.3-0ubuntu3.4), libgs9:amd64 (9.10~dfsg-0ubuntu10.3, 9.10~dfsg-0ubuntu10.4), hplip-data:amd64 (3.14.3-0ubuntu3.2, 3.14.3-0ubuntu3.4), ghostscript:amd64 (9.10~dfsg-0ubuntu10.3, 9.10~dfsg-0ubuntu10.4)
history.log.17.gz:Install: hplip:amd64 (3.14.3-0ubuntu3.2), update-inetd:amd64 (4.43, automatic), avahi-daemon:amd64 (0.6.31-4ubuntu1, automatic), libwebpmux1:amd64 (0.4.0-4, automatic), libsensors4:amd64 (3.3.4-2ubuntu1, automatic), libsane-hpaio:amd64 (3.14.3-0ubuntu3.2, automatic), python-pil:amd64 (2.3.0-1ubuntu3, automatic), python-pexpect:amd64 (3.1-1ubuntu0.1, automatic), libart-2.0-2:amd64 (2.3.21-2, automatic), libhpmud0:amd64 (3.14.3-0ubuntu3.2, automatic), python-renderpm:amd64 (3.0-1build1, automatic), libnss-mdns:amd64 (0.10-6, automatic), python-imaging:amd64 (2.3.0-1ubuntu3, automatic), libsnmp-base:amd64 (5.7.2~dfsg-8.1ubuntu3, automatic), python-reportlab-accel:amd64 (3.0-1build1, automatic), printer-driver-postscript-hp:amd64 (3.14.3-0ubuntu3.2, automatic), python-reportlab:amd64 (3.0-1build1, automatic), libfile-copy-recursive-perl:amd64 (0.38-1, automatic), sane-utils:amd64 (1.0.23-3ubuntu3.1, automatic), libavahi-core7:amd64 (0.6.31-4ubuntu1, automatic), printer-driver-hpcups:amd64 (3.14.3-0ubuntu3.2, automatic), hplip-data:amd64 (3.14.3-0ubuntu3.2, automatic), libsnmp30:amd64 (5.7.2~dfsg-8.1ubuntu3, automatic), libdaemon0:amd64 (0.14-2ubuntu1, automatic)
04:17 PM .../log/apt $ 

```

---

### Post by ajgreeny on 2016-05-26
Sid is using 14.04 which does not have a version of HPLIP that works with that printer, it needs 3.15.9 or newer, so the repos are no use to him.

I have used the hplip.run files many times in the past without problems, and it looks as if those two possible errors I mention above are the likely reason for his difficulty.

Let's see what he replies.

---

### Post by vasa1 on 2016-05-26
> **ajgreeny said:**
> Sid is using 14.04 which does not have a version of HPLIP that works with that printer, it needs 3.15.9 or newer, so the repos are no use to him.

I have used the hplip.run files many times in the past without problems, and it looks as if those two possible errors I mention above are the likely reason for his difficulty.

Let's see what he replies.

Thanks for the information! I didn't know that.

---

### Post by Sid_Smith on 2016-05-26
Thanks. Universe and multiverse were enabled. The package manager was probably from a previous attempt to run this script. The same problem happened and I pressed ctrl+c to quit and run the script again.

---

### Post by ajgreeny on 2016-05-27
So is it now fixed?

If so please mark as SOLVED from the Thread Tools menu up-top. It is a great help to users searching the forum.

---

