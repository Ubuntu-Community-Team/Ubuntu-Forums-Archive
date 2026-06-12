---
title: "HP DesktJet 3630 drivers missing dependencies on 17.04"
date: 2017-07-24
forum: Hardware
---

### Post by Drone4four on 2017-07-24
I recently reformatted Ubuntu 16.04 on my Desktop computer to 17.04.  It’s a nice upgrade.  The biggest trouble I am having making the migration is installing HP printer drivers.  From the official website, I located my printer model.  [According to the docs, it looks like HP supports 17.04]("http://hplipopensource.com/hplip-web/models/deskjet_aio/deskjet_3630_series.html"), but when I actually run the CLI installer, I am getting error message 100 (see near the bottom of this traceback):

```
 $ ./hplip-install                        

HP Linux Imaging and Printing System (ver. 3.17.6)
HPLIP Installer ver. 5.1

Copyright (c) 2001-15 HP Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

Installer log saved in: hplip-install_Mon-24-Jul-2017_15:34:57.log

/
[COLOR="#00FF00"]note: Defaults for each question are maked with a '*'. Press <enter> to accept the default.
[/COLOR] 

INSTALLATION MODE
-----------------
Automatic mode will install the full HPLIP solution with the most common options.
Custom mode allows you to choose installation options to fit specific requirements.

Please choose the installation mode (a=automatic*, c=custom, q=quit) : a

Initializing. Please wait...


INTRODUCTION
------------
This installer will install HPLIP version 3.17.6 on your computer.
Please close any running package management systems now (YaST, Adept, Synaptic, Up2date, etc).


DISTRO/OS CONFIRMATION
----------------------
Distro appears to be Ubuntu 17.04.

Is "Ubuntu 17.04" your correct distro/OS and version (y=yes*, n=no, q=quit) ? y


ENTER USER PASSWORD
-------------------
Please enter the sudoer (gnull)'s password: 
 

INSTALLATION NOTES
------------------
Enable the universe/multiverse repositories. Also be sure you are using the Ubuntu "Main" Repositories. See: https://help.ubuntu.com/community/Repositories/Ubuntu for more information.  Disable the CD-ROM/DVD source if you do not have the Ubuntu installation media inserted in the drive.

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
libcrypto           	 network              REQUIRED            
libnetsnmp-devel     network              REQUIRED            
Do you want to install these missing dependencies (y=yes*, n=no, q=quit) ? y


INSTALL MISSING REQUIRED DEPENDENCIES
-------------------------------------
[COLOR="#00FF00"]note: Installation of dependencies requires an active internet connection.[/COLOR]
[COLOR="#800080"]warning: Missing REQUIRED dependency: libcrypto (libcrypto - OpenSSL cryptographic library)
warning: Missing REQUIRED dependency: libnetsnmp-devel (libnetsnmp-devel - SNMP networking library development files)[/COLOR]


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
Running 'sudo apt-get install --assume-yes openssl'
Please wait, this may take several minutes...
Running 'sudo apt-get install --assume-yes libsnmp-dev'
Please wait, this may take several minutes...
error: Command failed. Re-try #1...
Running 'sudo apt-get install --assume-yes libsnmp-dev'
Please wait, this may take several minutes...
error: Command failed. Re-try #2...
Running 'sudo apt-get install --assume-yes libsnmp-dev'
Please wait, this may take several minutes...
error: Command failed. Re-try #3...
Running 'sudo apt-get install --assume-yes libsnmp-dev'
Please wait, this may take several minutes...
[COLOR="#FF0000"]error: Package install command failed with error code 100[/COLOR]
Would you like to retry installing the missing package(s) (y=yes*, n=no, q=quit) ? y
Running 'sudo apt-get install --assume-yes libsnmp-dev'
Please wait, this may take several minutes...
[COLOR="#FF0000"]error: Package install command failed with error code 100[/COLOR]
Would you like to retry installing the missing package(s) (y=yes*, n=no, q=quit) ? 
Running 'sudo apt-get install --assume-yes libsnmp-dev'
Please wait, this may take several minutes...
[COLOR="#FF0000"]error: Package install command failed with error code 100[/COLOR]
Would you like to retry installing the missing package(s) (y=yes*, n=no, q=quit) ? 
Running 'sudo apt-get install --assume-yes libsnmp-dev'
Please wait, this may take several minutes...
[COLOR="#FF0000"]error: Package install command failed with error code 100[/COLOR]
Would you like to retry installing the missing package(s) (y=yes*, n=no, q=quit) ? 
Running 'sudo apt-get install --assume-yes libsnmp-dev'
Please wait, this may take several minutes...
[COLOR="#FF0000"]error: Package install command failed with error code 100[/COLOR]
Would you like to retry installing the missing package(s) (y=yes*, n=no, q=quit) ? n
[COLOR="#800080"]warning: Some HPLIP functionality might not function due to missing package(s).[/COLOR]
Running 'sudo apt-get install --assume-yes snmp-mibs-downloader'
Please wait, this may take several minutes...
[COLOR="#FF0000"]error: A required dependency 'libcrypto (libcrypto - OpenSSL cryptographic library)' is still missing.
error: A required dependency 'libnetsnmp-devel (libnetsnmp-devel - SNMP networking library development files)' is still missing.[/COLOR]


RUNNING POST-PACKAGE COMMANDS
-----------------------------
OK


RE-CHECKING DEPENDENCIES
------------------------
[COLOR="#FF0000"]error: A required dependency 'libcrypto (libcrypto - OpenSSL cryptographic library)' is still missing.
error: A required dependency 'libnetsnmp-devel (libnetsnmp-devel - SNMP networking library development files)' is still missing.
error: Installation cannot continue without these dependencies.
error: Please manually install this dependency and re-run this installer.[/COLOR]
$ 
```

***Note: I preserved text colors here on the forum based on how it appears in my terminal

When I Google around with ‘error: Package install command failed with error code 100’, users report issues with dependencies but these results are forum threads from 2014 or earlier, nothing specific to 17.04 or ‘libcrypto’ or ‘libnetsnmp-devel’ which is the problem spot in my case.  

I encountered a launchpad support thread from with similar issues with the same dependencies as mine however its dated 2007! =/

---

### Post by vocx on 2017-07-24
First of all, according to the HP website, your HP 3630 is supported by version 3.15.6 of HPLIP. This is the minimum version, which means any newer version should work as well. The terminal output that you are showing seems to be the output of the installation script for HPLIP 3.17.6. That is, you are attempting to install a newer HPLIP. However, I don't think you need to install this newer version, as Ubuntu 17.04 already has in its repositories a version of HPLIP that should be enough to run your printer. According to [https://packages.ubuntu.com/](https://packages.ubuntu.com/) Ubuntu 17.04 has HPLIP version 3.16.11.
```

apt show hplip
sudo apt install hplip

```

Once you have installed "hplip" from the repositories, now you can install your printer. Connect it to the computer by USB or put it in the same local network through Ethernet, and turn it on.
```

hp-setup

```
If there are missing dependencies install those dependencies.

Did you get that? There are two things. One is the HPLIP package itself. It is a collection of drivers and tools to make your printer work. You don't need the newest one, you only need a version that is sufficiently recent to support your printer. Ubuntu already includes one version (slightly old but sufficient). When you install that, then you just need to run "hp-setup" to actually install your HP printer.

Some references
[https://ubuntuforums.org/showthread.php?t=2364149&p=13658387#post13658387](https://ubuntuforums.org/showthread.php?t=2364149&p=13658387#post13658387)
[https://ubuntuforums.org/showthread.php?t=2366396&p=13667712#post13667712](https://ubuntuforums.org/showthread.php?t=2366396&p=13667712#post13667712)

---

### Post by Drone4four on 2017-07-24
Thank you **@vocx** for your advice.  Installing hplip from the official Ubuntu repos was a sinch.  After running hp-setup, a few seconds later I had successfully printed a test page.  That was so much easier than downloading and playing with the drivers directly from HP's website.

---

### Post by vocx on 2017-07-24
> **Drone4four said:**
> Thank you **@vocx** for your advice.  Installing hplip from the official Ubuntu repos was s inch.  After running hp-setup, a few seconds later I had successfully printed a test page.  That was so much easier than downloading and playing with the drivers directly from HP's website.
Correct. Ubuntu includes many things in its repositories. You should always look for software in the repositories before trying to install from a particular project's website. Installing from a website is only necessary when the version in the repositories is much older than what you need.

---

