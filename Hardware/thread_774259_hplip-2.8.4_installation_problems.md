---
title: "hplip-2.8.4 installation problems"
date: 2008-04-29
forum: Hardware
---

### Post by DamonChyld on 2008-04-29
The hplip-2.8.4 installer for my HP printer is telling me that I need to install cups. Libcups2 seems to be installed, both here when I run apt-get and in synaptic.

```

:~/Desktop$ sudo apt-get install --yes --force-yes libcupsys2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libcupsys2 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

I have tried to reinstall it, but receive the same error.

```


RUNNING PRE-INSTALL COMMANDS
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
sudo dpkg --configure -a (Pre-depend step 1)
sudo apt-get install --yes --force-yes -f (Pre-depend step 2)
sudo apt-get update (Pre-depend step 3)


DEPENDENCY AND CONFLICT RESOLUTION
----------------------------------
Running 'sudo apt-get install --yes --force-yes libcupsys2'
Please wait, this may take several minutes...
Running 'sudo apt-get install --yes --force-yes libsane'
Please wait, this may take several minutes...
 

RUNNING POST-PACKAGE COMMANDS
-----------------------------


RE-CHECKING DEPENDENCIES
------------------------
error: A required dependency 'cups (cups - Common Unix Printing System)' is still missing.
error: Installation cannot continue without this dependency.
error: Please manually install this dependency and re-run this installer.
```

I would really appreciate any help, I am not sure how to move forward on this.

---

### Post by DamonChyld on 2008-05-02
Kindly [COLOR="Sienna"]B[/COLOR]ring [COLOR="Sienna"]U[/COLOR]p [COLOR="Sienna"]M[/COLOR]y [COLOR="Sienna"]P[/COLOR]ost

---

