---
title: "HP Printer, HPLIP and CUPS!!"
date: 2007-12-07
forum: Hardware &amp; Laptops
---

### Post by whos2know on 2007-12-07
Hi!  I really hope someone can help me!!!  I just purchased a HP Officejet C4085.  I've installed  hplip-2.7.10.run and I have installed CUPS even though seems that the Hplip don't seem to see that I have.  I am completely lost and any help would be great!!  Here is my output from su hplip-2.7.10.run.  Thank you very much!!

[PHP]RUNNING PRE-INSTALL COMMANDS
----------------------------


INSTALL MISSING REQUIRED DEPENDENCIES
-------------------------------------
warning: There are 1 missing REQUIRED dependencies.
note: Installation of dependencies requires an active internet connection.
warning: Missing REQUIRED dependency: cups (cups - Common Unix Printing System)


INSTALL MISSING OPTIONAL DEPENDENCIES
-------------------------------------
warning: There are 1 missing OPTIONAL dependencies.
note: Installation of dependencies requires an active internet connection.
warning: Missing OPTIONAL dependency for option 'scan': scanimage (scanimage - Shell scanning program)


CHECKING FOR NETWORK CONNECTION
-------------------------------
Network connection present.


RUNNING PRE-PACKAGE COMMANDS
----------------------------
warning: An error occurred running 'sudo dpkg --configure -a'
sudo dpkg --configure -a (Pre-depend step 1)
warning: An error occurred running 'sudo apt-get install --yes --force-yes -f'
sudo apt-get install --yes --force-yes -f (Pre-depend step 2)
warning: An error occurred running 'sudo apt-get update'
sudo apt-get update (Pre-depend step 3)


DEPENDENCY AND CONFLICT RESOLUTION
----------------------------------
Running 'sudo apt-get install --yes --force-yes libcupsys2 libsane'
Please wait, this may take several minutes...
error: Package install command failed with error code 100
Would you like to retry installing the missing package(s) (y=yes*, n=no, q=quit) ? 
Running 'sudo apt-get install --yes --force-yes libcupsys2 libsane'
Please wait, this may take several minutes...
error: Package install command failed with error code 100
Would you like to retry installing the missing package(s) (y=yes*, n=no, q=quit) ? n
warning: Some HPLIP functionality might not function due to missing package(s).
warning: A previous install of HPLIP is installed and/or running.
sudo apt-get remove --yes --force-yes hplip hpijs (Removing old HPLIP version)
warning: HPLIP removal failed. The previous install may have been installed using a tarball or this installer.
warning: Continuing to run installer - this installation should overwrite the previous one.
error: A required dependency 'cups (cups - Common Unix Printing System)' is still missing.
error: Installation cannot continue without this dependency.
error: Please manually install this dependency and re-run this installer.
[/PHP]

---

### Post by whos2know on 2007-12-09
Anyone?? Please help.... I need my printer.. Thanx!!

---

### Post by Melcar on 2007-12-09
If I'm not mistaken, HPLIP should be in the repos.  Also, you should be running it as:

sudo sh hplip-2.7.10.run

---

### Post by whos2know on 2007-12-10
Yes. it is in the Repos.... and installed...and reinstalled....but it doesn't want to find my printer when I run Hp-setup it finds my Printer, and I get this response...

[PHP]bobby@TheOne:~/Desktop$ sudo hp-setup

HP Linux Imaging and Printing System (ver. 2.7.10)
Printer/Fax Setup Utility ver. 7.0

Copyright (c) 2001-7 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

error: PPD not file found.An appropriate PPD file could not be found. Please check your HPLIP install, use <i>Select Other...</i>, or download one from linuxprinting.org.
[/PHP]

Thank you for replying.... I have been searching up and down the net for help.... any help thanx again!!

Bobby

PS yes I did use sudo sh hplip-2.7.10.run.  Thank you again!!

---

### Post by stchman on 2007-12-13
> **whos2know said:**
> Hi!  I really hope someone can help me!!!  I just purchased a HP Officejet C4085.  I've installed  hplip-2.7.10.run and I have installed CUPS even though seems that the Hplip don't seem to see that I have.  I am completely lost and any help would be great!!  Here is my output from su hplip-2.7.10.run.  Thank you very much!!

[PHP]RUNNING PRE-INSTALL COMMANDS
----------------------------


INSTALL MISSING REQUIRED DEPENDENCIES
-------------------------------------
warning: There are 1 missing REQUIRED dependencies.
note: Installation of dependencies requires an active internet connection.
warning: Missing REQUIRED dependency: cups (cups - Common Unix Printing System)


INSTALL MISSING OPTIONAL DEPENDENCIES
-------------------------------------
warning: There are 1 missing OPTIONAL dependencies.
note: Installation of dependencies requires an active internet connection.
warning: Missing OPTIONAL dependency for option 'scan': scanimage (scanimage - Shell scanning program)


CHECKING FOR NETWORK CONNECTION
-------------------------------
Network connection present.


RUNNING PRE-PACKAGE COMMANDS
----------------------------
warning: An error occurred running 'sudo dpkg --configure -a'
sudo dpkg --configure -a (Pre-depend step 1)
warning: An error occurred running 'sudo apt-get install --yes --force-yes -f'
sudo apt-get install --yes --force-yes -f (Pre-depend step 2)
warning: An error occurred running 'sudo apt-get update'
sudo apt-get update (Pre-depend step 3)


DEPENDENCY AND CONFLICT RESOLUTION
----------------------------------
Running 'sudo apt-get install --yes --force-yes libcupsys2 libsane'
Please wait, this may take several minutes...
error: Package install command failed with error code 100
Would you like to retry installing the missing package(s) (y=yes*, n=no, q=quit) ? 
Running 'sudo apt-get install --yes --force-yes libcupsys2 libsane'
Please wait, this may take several minutes...
error: Package install command failed with error code 100
Would you like to retry installing the missing package(s) (y=yes*, n=no, q=quit) ? n
warning: Some HPLIP functionality might not function due to missing package(s).
warning: A previous install of HPLIP is installed and/or running.
sudo apt-get remove --yes --force-yes hplip hpijs (Removing old HPLIP version)
warning: HPLIP removal failed. The previous install may have been installed using a tarball or this installer.
warning: Continuing to run installer - this installation should overwrite the previous one.
error: A required dependency 'cups (cups - Common Unix Printing System)' is still missing.
error: Installation cannot continue without this dependency.
error: Please manually install this dependency and re-run this installer.
[/PHP]

I went to HP's website and could find NOTHING on an officejet c4085.  Are you sure you gave us the right model?

---

### Post by whos2know on 2007-12-14
sorry about that... it's a HP C4385.. Thank you for any help!!! :D and happy holidays!!

---

### Post by whos2know on 2008-01-03
bump

---

### Post by Thund3rstruck on 2008-01-11
Yea, I'm in a similar boat. I have an HP LaserJet Pro L7650 and the Ubuntu tool won't find the printer. When I run HP's official Ubuntu installer I get this error

```

Running 'sudo apt-get install --yes --force-yes python2.5-dev libcupsys2-dev cupsys-bsd libusb-dev libtool libjpeg62-dev openssl libsnmp9-dev python-qt3 python-reportlab libsane-dev libsane'
Please wait, this may take several minutes...
error: Package install command failed with error code 100
Would you like to retry installing the missing package(s) (y=yes*, n=no, q=quit) ? 

```
It never gets past that and I have no printing ability

---

### Post by FatAngus on 2008-01-11
I'm also getting the same error message trying to install HP Photosmart C6280 All-in-One. :confused:

Any help would really be appreciated and thanks in advance :)

---

### Post by Sef on 2008-01-12
Check out the [HPLIP website]("http://hplip.sourceforge.net/index.html").

---

### Post by Thund3rstruck on 2008-01-13
> **Sef said:**
> Check out the [HPLIP website]("http://hplip.sourceforge.net/index.html").

yea, yea been there done that. 

I actually did get it to work finally. When you run the install script from the website mentioned above before it errors out it does a full un-install of the previous package. After the install errors out re-install the package with aptitude. After this hp-setup magically works!

---

### Post by whos2know on 2008-02-08
fixed!  I just cloned ubuntu and reinstalled it.... thanks for all the help!

---

### Post by jatatar on 2008-04-07
fatangus

in gnome, just use the printer/setup option in System>Printers menu,  I have this same printer plugged in to network router.  During setup, choose appsocket / hp jet direct...manually enter ip address.   This can be found looking at network settings on the printer itself...then choose HP, then choose photosmart c6100.

If this is used on a windows box too, you will have to reinstall according to network setup for windows also, but this is the only way i could get it to work.
joe

---

### Post by kevindt on 2008-04-10
With regard to the L7600 series multi-function printers mentioned above:

Using the Hardy beta with all current updates, _hplip-gui_ was easily selected with Synaptic and installed without problems.  HPLIP Toolbox then appeared on the System>Preferences menu and I walked pretty effortlessly though installation of my network-connected OfficePro L7680, enabling scan, fax, print and photocard services.  The current version in the repo had the correct .ppd for this printer

---

