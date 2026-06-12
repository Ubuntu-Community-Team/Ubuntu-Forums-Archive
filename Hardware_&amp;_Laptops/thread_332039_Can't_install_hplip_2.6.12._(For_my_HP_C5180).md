---
title: "Can't install hplip 2.6.12. (For my HP C5180)"
date: 2007-01-05
forum: Hardware &amp; Laptops
---

### Post by emil.s on 2007-01-05
Hello!
I'm trying to install hplip-2.6.12, to get my HP Photosmart work. It seems like 2.6.9 (in APT) not is working, even if it should...

But when i try to install the new version from sourceforge i get this:
```
root@Sandnabba: /home/emil # ./hplip-1.6.12.run 
Creating directory hplip-1.6.12
Verifying archive integrity... All good.
Uncompressing HPLIP 1.6.12 Self Extracting Archive...................................................................................................................
..............................................................................................................................
..............................................................................................................................
..............................................................................................................................
..............................................................................................................................


HP Linux Imaging and Printing System (ver. 1.6.12)
HPLIP Installer ver. 1.0

Copyright (c) 2003-6 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.
                                                                                                                                                                    Initializing...   

note: Defaults for each question are maked with a '*'. Press <enter> to accept the default.


INSTALLATION MODE
-----------------
Please choose the installation mode (a=automatic*, c=custom, q=quit) : 

This installer will install HPLIP version 1.6.12 on your computer.
Distro is Ubuntu 6.10


DISTRO/OS SELECTION
-------------------

Is "Ubuntu 6.10" your correct distro/OS and version (y=yes*, n=no, q=quit) ? 


INSTALLATION NOTES
------------------
Before proceeding please enable the universe/multiverse repositories in Synaptic or Apt.  In addition disable the Ubuntu CD source. https://help.ubuntu.com/community/Repositories for more information.

Please read the installation notes and hit <enter> to continue (<enter>=continue*, q=quit) : 

INSTALL MISSING REQUIRED DEPENDENCIES
-------------------------------------

warning: There are 1 missing REQUIRED dependencies.
note: Installation of dependencies requires an active internet connection.
warning: Missing REQUIRED dependency: cups (cups - Common Unix Printing System)
----------

Running 'sudo dpkg --configure -a && sudo apt-get update'
Please wait, this may take several minutes...                                                                                                                                         

DEPENDENCY AND CONFLICT RESOLUTION
----------------------------------
Running 'sudo apt-get install --force-yes --yes libcupsys'
Please wait, this may take several minutes...                                                                                                                                        error: Package install command failed with error code 100
Would you like to retry installing the missing package(s)? (y=yes*, n=no, q=quit) : 
Running 'sudo apt-get install --force-yes --yes libcupsys'
Please wait, this may take several minutes...                                                                                                                                        error: Package install command failed with error code 100
Would you like to retry installing the missing package(s)? (y=yes*, n=no, q=quit) : 
```

I have done "apt-get install libcups*", but it's still the same... :(

Anyone who know?

---

### Post by 11hjpphty76lkjj on 2007-01-12
Try 

```
sudo apt-get install libcupsys2-devel
```

A

---

### Post by gabbman on 2007-01-30
I downloaded the hplip-1.7.1 from sourceforge, extacted the file to my home direcory, opened the terminal changed to the hplip-1.7.1 directory, and ran sudo ./hplip-install then my password, and the ease of ubuntu and sorcefoge took over to configure, make, build and install all the files until a pop up window asked me some simple questions as to how I wanted it installed (direct wireless to the ethernet) and I'm up and running and scanning with my C5180 on 6.06.

---

### Post by 11hjpphty76lkjj on 2007-01-30
Great! I'm glad the updates worked.  Any thoughts on where I can improve the installer?

A

---

### Post by gabbman on 2007-02-01
> **kalosaurusrex said:**
> Great! I'm glad the updates worked.  Any thoughts on where I can improve the installer?

AIt's hard to improve on something that just works.  Perhaps the gang at automaix2 could script it into automatix2 as a selection for those who have these printers.

---

### Post by emil.s on 2007-02-02
It's not working fo me... :(
And now i get a new computer with a clean install...

```
root@servern: /home/emil/hplip-1.7.1 # ./hplip-install 
warning: Config file /etc/hp/hplip.conf not found or not readable.

HP Linux Imaging and Printing System (ver. 1.7.1)
HPLIP Installer ver. 1.0

Copyright (c) 2003-6 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.
                                                                                                                                                                    Initializing...   

note: Defaults for each question are maked with a '*'. Press <enter> to accept the default.


INSTALLATION MODE
-----------------
Please choose the installation mode (a=automatic*, c=custom, q=quit) : 

This installer will install HPLIP version 1.7.1 on your computer.
Distro is Ubuntu 6.10


DISTRO/OS SELECTION
-------------------

Is "Ubuntu 6.10" your correct distro/OS and version (y=yes*, n=no, q=quit) ? 


INSTALLATION NOTES
------------------
Enable the universe/multiverse repositories. See: https://help.ubuntu.com/community/Repositories/Ubuntu for more information.

Please read the installation notes and hit <enter> to continue (<enter>=continue*, q=quit) : 

INSTALL MISSING REQUIRED DEPENDENCIES
-------------------------------------

warning: There are 1 missing REQUIRED dependencies.
note: Installation of dependencies requires an active internet connection.
warning: Missing REQUIRED dependency: cups (cups - Common Unix Printing System)
----------

Running 'sudo dpkg --configure -a'
Please wait, this may take several minutes...                                                                                                                                        Running 'sudo apt-get install -f'
Please wait, this may take several minutes...                                                                                                                                        Running 'sudo apt-get update'
Please wait, this may take several minutes...                                                                                                                                        Running 'xterm -e sudo apt-get install postfix'
Please wait, this may take several minutes...


DEPENDENCY AND CONFLICT RESOLUTION
----------------------------------
Running 'sudo apt-get install --force-yes --yes libcupsys2'
Please wait, this may take several minutes...                                                                                                                          error: A required dependency 'cups' is still missing.
error: Installation cannot continue without this dependency. Please manually install this dependency and re-run this installer.
```

I have tried with both the tarball and the self-extracting installer.

But it is installed:
```

root@servern: /home/emil/hplip-1.7.1 # apt-get install libcupsys2
Läser paketlistor... Färdig
Bygger beroendeträd         
Reading state information... Färdig
libcupsys2 är redan den senaste versionen.
0 uppgraderade, 0 nyinstallerade, 0 att ta bort och 0 ej uppgraderade.
root@servern: /home/emil/hplip-1.7.1 # apt-get install libcupsys2-dev 
Läser paketlistor... Färdig
Bygger beroendeträd         
Reading state information... Färdig
libcupsys2-dev is alredy the latest avlilable version.
0 uppgraderade, 0 nyinstallerade, 0 att ta bort och 0 ej uppgraderade.
```

---

### Post by gabbman on 2007-02-03
> **kalosaurusrex said:**
> Great! I'm glad the updates worked.  Any thoughts on where I can improve the installer?

A
On my daughters dell 4500 an HP icon was created in the >Applications >Accessories menu, on my Sony Vaio there is no icon. Both running 6.06 LTS.

I was interested to test it from the Control Center on the Heard CD, but when you click the icon in the Control Center nothing launches.

I just discovered, Herd 3 does not have lipcups2 dev and PyQt installed.  Which explains why hplip does not work from the control center in Herd 3.

---

### Post by emil.s on 2007-02-04
> **gabbman said:**
> On my daughters dell 4500 an HP icon was created in the >Applications >Accessories menu, on my Sony Vaio there is no icon. Both running 6.06 LTS.

I was interested to test it from the Control Center on the Heard CD, but when you click the icon in the Control Center nothing launches.
I have the same problem. I tested "Herd 3"... And i get the same error in school with anoter CD. So it must be a bug. Try with some later daily buid.
And tell me if it works! :)

---

### Post by mags73 on 2007-03-11
> **gabbman said:**
> It's hard to improve on something that just works.  Perhaps the gang at automaix2 could script it into automatix2 as a selection for those who have these printers.

I have to say, I have to agree with gabbman, that was the easiest install for my OfficeJet 6300.  It is hard to improve something that just works.  I would even go out on a limb and say that I think it was even easier than the OEM version under Windows.  Thank you for making our lives easier :)

---

### Post by 11hjpphty76lkjj on 2007-03-23
> **gabbman said:**
> On my daughters dell 4500 an HP icon was created in the >Applications >Accessories menu, on my Sony Vaio there is no icon. Both running 6.06 LTS.

I was interested to test it from the Control Center on the Heard CD, but when you click the icon in the Control Center nothing launches.

I just discovered, Herd 3 does not have lipcups2 dev and PyQt installed.  Which explains why hplip does not work from the control center in Herd 3.

Yes I've seen that the HP icon does not work in the control center.  The problem is that pyqt is not being preinstalled with Herd.  We've let the ubuntu team know.  Although I'm not sure if/when this will be fixed.

---

### Post by NewJack on 2007-03-25
Just wanted to thank gabbman.  I was having a problem installing my HP LaserJet 1200 and did the install the way he said and had no problems.  Sorry to hijack, but just wanted to say thanks.

---

