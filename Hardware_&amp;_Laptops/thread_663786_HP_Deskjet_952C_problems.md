---
title: "HP Deskjet 952C problems"
date: 2008-01-10
forum: Hardware &amp; Laptops
---

### Post by Joseph Elliott on 2008-01-10
My printer was working last night then I changed the black cartridge.  Now it refuses to print black.  A test page results in a grey scale that will only go to 90%.  I uninstalled the printer and reinstalled it with the same results.  The new cartridge instruction say to:
1. Press the print-head against a damp warm paper towel for 3 seconds.
2. Dry the print head by dabbing it with a paper towel.
3. Run 2 cleaning cycles on your printer.

I did steps one and two but my printer menu doesn't give me the option of cleaning.  The button is there but it is not accessible - can't click on it.

I then searched these forums and downloaded the newest driver ([http://hplip.sourceforge.net/downloads.html](http://hplip.sourceforge.net/downloads.html)) but I got the following when I put it into terminal:

> joseph@joseph-desktop:~$ sudo sh hplip-2.7.12.run
[sudo] password for joseph:
Creating directory hplip-2.7.12
Verifying archive integrity... All good.
Uncompressing HPLIP 2.7.12 Self Extracting Archive.................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................

HP Linux Imaging and Printing System (ver. 2.7.12)
HPLIP Installer ver. 3.0

Copyright (c) 2001-7 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

Installer log saved in: hplip-install_Thu-10-Jan-2008_11:36:12.log

|error: You are running the installer as root. It is highly recommended that you run the installer as
error: a regular (non-root) user. Do you still wish to continue?
Continue with installation (y=yes, n=no*, q=quit) ? y

note: Defaults for each question are maked with a '*'. Press <enter> to accept the default.


INSTALLATION MODE
-----------------
Automatic mode will install the full HPLIP solution with the most common options.
Custom mode allows you to chose installation options to fit specific requirements.

Please choose the installation mode (a=automatic*, c=custom, w=web installer, q=quit) : a

Initializing. Please wait...
 

INTRODUCTION
------------
This installer will install HPLIP version 2.7.12 on your computer.
Please close any running package management systems now (YaST, Adept, Synaptic, Up2date, etc).


DISTRO/OS CONFIRMATION
----------------------
Distro appears to be Ubuntu 7.10.

Is "Ubuntu 7.10" your correct distro/OS and version (y=yes*, n=no, q=quit) ? y


INSTALLATION NOTES
------------------
Enable the universe/multiverse repositories. See: [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu) for more information.  Disable the CD-ROM/DVD source if you do not have the Ubunbtu installation media inserted in the drive.

Please read the installation notes. Press <enter> to continue or 'q' to quit: 


RUNNING PRE-INSTALL COMMANDS
----------------------------


INSTALL MISSING OPTIONAL DEPENDENCIES
-------------------------------------
warning: There are 3 missing OPTIONAL dependencies.
note: Installation of dependencies requires an active internet connection.
warning: Missing REQUIRED dependency for option 'network': libcrypto (libcrypto - OpenSSL cryptographic library)
warning: Missing REQUIRED dependency for option 'network': libnetsnmp-devel (libnetsnmp-devel - SNMP networking library development files)
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
Running 'sudo apt-get install --yes --force-yes openssl libsnmp9-dev libsane'
Please wait, this may take several minutes...
error: Package install command failed with error code 100
Would you like to retry installing the missing package(s) (y=yes*, n=no, q=quit) ? y



I'm running Ubuntu 7.10 if it makes a difference.  Any ideas on what went wrong?

Joseph

---

### Post by esmerine on 2008-01-10
I'm trying to install driver for my psc1210 (to have a working scanner) but I'm also getting "Error code 100".

edit: Whoops, I haven't noticed there was a XSane image scanner. But I downloaded hplip-gui, don't know if I really had to do this. Scanning perfectly with automatically installed hplip-2.7.7. Although printer says that it is low on ink it still prints well. But maybe it won't someday. Will this new driver actually help?

---

