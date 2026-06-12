---
title: "HP Printer"
date: 2014-09-03
forum: Hardware
---

### Post by skyesharica on 2014-09-03
Dear Linux Friends,

There is a fault with Hewlett Packard printer software.  Someone told me to run some code here.  I never do this because I have NO coding knowledge, but for some odd reason I did.  Even though I am very very ill and desperately need the office to work ... for basic necessities.

Now my printer has gone completely and I cannot download any driver - old or latest.

Can someone skilful please have a look at this post and send me technical assistance?

[http://ubuntuforums.org/showthread.php?t=2242381](http://ubuntuforums.org/showthread.php?t=2242381)

Apparently, because of what this member made me do the software I have, I have to manually install a dependency.:

error: A required dependency 'cups-image (CUPS image - CUPS image development files)' is still missing.
error: Installation cannot continue without this dependency.
error: Please manually install this dependency and re-run this installer.

I HAVE ABSOLUTELY NO IDEA HOW 2 DO THIS and don't want to trust a less merciful member again.

Please help?

---

### Post by christopher9 on 2014-09-03
It appears that you are using Ubuntu 14.04 'Trusty"...

---

### Post by Yellow Pasque on 2014-09-04
> error: A required dependency 'cups-image (CUPS image - CUPS image development files)' is still missing.
The command to resolve that (sudo apt-get install libcupsimage2-dev) was actually given in the previous thread.

Of course, now you have bigger dependency problems because installing an old hplip version was a bad idea/suggestion. I think I would remove all instances of hplip packages to tackle this issue.
```
sudo apt-get purge hplip*
```

---

### Post by skyesharica on 2014-10-10
Hi [[IMG]http://ubuntuforums.org/customavatars/avatar1924438_1.gif[/IMG]]("http://ubuntuforums.org/member.php?u=1924438") [christopher9]("http://ubuntuforums.org/member.php?u=1924438") and [[IMG]http://ubuntuforums.org/customavatars/avatar327594_14.gif[/IMG]]("http://ubuntuforums.org/member.php?u=327594") [Temüjin]("http://ubuntuforums.org/member.php?u=327594")

My apologies for not answering sooner.  I've been very ill and unable to respond.  It looks like a disaster.

Firstly, yes, Rich, it appears that the scanner function is simply not working now.  So that is Hewlett Packard's fault.  

Then, it appears that I stuffed the software by trying to install a  previous version ... older versions are available at the website ... so  this is Hewlett Packard's fault again.  This is when I got the error  message about the missing dependency:  libcupsimage2-dev.  I've never  had that error before, so it is a fault with the driver software ...  perhaps it is not up to date with Ubuntu 14.04 LTS.

Then, I tried all the tips--which I assume were most kindly given.   Like: sudo apt-get update ... sudo apt-get install libcupsimage2-dev.   And:  sudo apt-get install -f ... sudo apt-get install libcups2*.  No  matter what I tried, I always got similar screens to these - about the  missing dependency and two missing optional dependencies for scanning.   Then the mess up continues with further screens about broken up  software.

[[IMG]http://ubuntuforums.org/attachment.php?attachmentid=257095&d=1412948470&thumb=1[/IMG]]("http://ubuntuforums.org/attachment.php?attachmentid=257095&d=1412948470")
[[IMG]http://ubuntuforums.org/attachment.php?attachmentid=257096&d=1412948575&thumb=1[/IMG]]("http://ubuntuforums.org/attachment.php?attachmentid=257096&d=1412948575")
[[IMG]http://ubuntuforums.org/attachment.php?attachmentid=257098&d=1412949081&thumb=1[/IMG]]("http://ubuntuforums.org/attachment.php?attachmentid=257098&d=1412949081")
[[IMG]http://ubuntuforums.org/attachment.php?attachmentid=257100&d=1412949491&thumb=1[/IMG]]("http://ubuntuforums.org/attachment.php?attachmentid=257100&d=1412949491")

I've since been sent an upgrade notice for hplip 3.14.10 and it still doesn't work ... same error messages.

Then I tried to clean up the damage done, as you were right, my general  updates were affected.  I thought it was better to keep a good Ubuntu  than a bad printer.  My updates started requesting "partial" etc.  So I  decided you were right - [pqwoerituytrueiwoq]("http://ubuntuforums.org/member.php?u=865458") when you said:  "but  if you still have broken packages you cant install ANYTHING no even  updates".  So I did the PURGE command:  sudo apt-get purge hplip*.  This  is the copy of the terminal.:
```

mofa511@mofa511-TravelMate-X483:~$ sudo apt-get purge hplip*
[sudo] password for mofa511: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'hplip' for regex 'hplip*'
Note, selecting 'hplip-ppds' for regex 'hplip*'
Note, selecting 'hplip-dbg' for regex 'hplip*'
Note, selecting 'hplip-doc' for regex 'hplip*'
Note, selecting 'hplip-data' for regex 'hplip*'
Note, selecting 'hplip-cups' for regex 'hplip*'
Note, selecting 'hplip-gui' for regex 'hplip*'
Package 'hplip-cups' is not installed, so not removed
Note, selecting 'hpijs-ppds' instead of 'hplip-ppds'
Package 'hplip-dbg' is not installed, so not removed
Package 'hplip-doc' is not installed, so not removed
Package 'hplip-gui' is not installed, so not removed
The following packages were automatically installed and are no longer required:
  linux-headers-3.13.0-32 linux-headers-3.13.0-32-generic
  linux-image-3.13.0-32-generic linux-image-extra-3.13.0-32-generic
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  hplip* hplip-data* printer-driver-postscript-hp*
0 to upgrade, 0 to newly install, 3 to remove and 31 not to upgrade.
After this operation, 11.3 MB disk space will be freed.
Do you want to continue? [Y/n] Y
(Reading database ... 232099 files and directories currently installed.)
Removing printer-driver-postscript-hp (3.14.3-0ubuntu3.2) ...
Removing hplip (3.14.3-0ubuntu3.2) ...
Purging configuration files for hplip (3.14.3-0ubuntu3.2) ...
Removing hplip-data (3.14.3-0ubuntu3.2) ...
Processing triggers for cups (1.7.2-0ubuntu1.2) ...
Processing triggers for man-db (2.6.7.1-1) ...
mofa511@mofa511-TravelMate-X483:~$ apt-get autoremove
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
mofa511@mofa511-TravelMate-X483:~$ 
```

AND YES, IT DID WORK ... I NOW HAVE NO PRINTER ... I AM PURGED OF DRIVER SOFTWARE.

I tried to install the CUPS whatever:  
&#8220;cups&#8221; 1.7.2-0ubuntu1.1 source package in Ubuntu

I was told I needed the version with the word "deb" in it.  So I got this one.:

[cups_1.7.2-0ubuntu1.1.debian.tar.gz]("https://launchpad.net/ubuntu/+archive/primary/+files/cups_1.7.2-0ubuntu1.1.debian.tar.gz")

It didn't work.  I downloaded the GDebi software and tried to open it  but it said:  "not a Debian package".  (Hey, I don't even know what  Debian means.)  See below.

[[IMG]http://ubuntuforums.org/attachment.php?attachmentid=257102&d=1412950564&thumb=1[/IMG]]("http://ubuntuforums.org/attachment.php?attachmentid=257102&d=1412950564")

Thank heavens though - PERHAPS - my software is no longer faulty.  I  still have a missing dependency but I don't get the UPDATER error  message of REQUIRING A PARTIAL UPGRADE (due to software problems).  I  get all the updates.  I looked closely - and saw some of the updates had  the word "image", like "linux-image-extra-3.13.0.37-generic".  But it  made no difference.  

I then tried to install the latest driver again.  But it made no  difference.  It had the same error message:  "Missing REQUIRED  dependency: cups-image (CUPS image - CUPS image development files)".  I  don't know if this means that my regular software updates will be  affected in future.  Here is a copy of the Terminal commands.:
```

mofa511@mofa511-TravelMate-X483:~$ cd /home/mofa511/Desktop
mofa511@mofa511-TravelMate-X483:~/Desktop$ sh hplip-3.14.10.run
Creating directory hplip-3.14.10
Verifying archive integrity... All good.
Uncompressing HPLIP 3.14.10 Self Extracting  Archive...........................................   ..................................................   ..................................................   ..................................................   ..................................................   ..................................................   ..................................................   ..................................................   ..................................................   ..................................................   ..................................................   ..................................................   ..................................................   ..................................................   ..................................................   ..................................................   ..................................................   ..................................................   ..................................................   ..................................................   ..................................................   ..................................................   ..................................................   ..................................................   ..................................................   ..................................................   ..................................................   ..................................................   ..................................................   ..................................................   ..................................................   ..................................................   ..................................................   ..................................................   ..................................................   ..................................................   ..................................................   ..................................................   ..................................................   ..................................................   ..................................................   ..................................................   ..................................................   ..................................................   ..................................................   ..................................................   ..................................................   ..................................................   ..................................................   ..................................................   ..................................................   ..................................................   ..................................................   ..................................................   ..................................................   ..................................................   ..................................................   ..................................................   ..............................................

HP Linux Imaging and Printing System (ver. 3.14.10)
HPLIP Installer ver. 5.1

Copyright (c) 2001-13 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

Installer log saved in: hplip-install_Fri-10-Oct-2014_04:20:02.log

\
note: Defaults for each question are maked with a '*'. Press <enter> to accept the default.
 

INSTALLATION MODE
-----------------
Automatic mode will install the full HPLIP solution with the most common options.
Custom mode allows you to choose installation options to fit specific requirements.

Please choose the installation mode (a=automatic*, c=custom, q=quit) : a

Initializing. Please wait...


INTRODUCTION
------------
This installer will install HPLIP version 3.14.10 on your computer.
Please close any running package management systems now (YaST, Adept, Synaptic, Up2date, etc).
 

DISTRO/OS CONFIRMATION
----------------------
Distro appears to be Ubuntu 14.04.

Is "Ubuntu 14.04" your correct distro/OS and version (y=yes*, n=no, q=quit) ? y


ENTER USER PASSWORD
-------------------
Please enter the sudoer (mofa511)'s password: 
 

INSTALLATION NOTES
------------------
Enable the universe/multiverse repositories. Also be sure you are using the Ubuntu "Main" Repositories. See: [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu) for more information.  Disable the CD-ROM/DVD source if you do not have the Ubuntu installation media inserted in the drive.

Please read the installation notes. Press <enter> to continue or 'q' to quit: 


RUNNING PRE-INSTALL COMMANDS
----------------------------
OK


INSTALL MISSING REQUIRED DEPENDENCIES
-------------------------------------
warning: There are 1 missing REQUIRED dependencies.
note: Installation of dependencies requires an active internet connection.
warning: Missing REQUIRED dependency: cups-image (CUPS image - CUPS image development files)


INSTALL MISSING OPTIONAL DEPENDENCIES
-------------------------------------
warning: There are 2 missing OPTIONAL dependencies.
note: Installation of dependencies requires an active internet connection.
warning: Missing REQUIRED dependency for option 'scan': sane-devel (SANE - Scanning library development files)
warning: Missing OPTIONAL dependency for option 'scan': xsane (xsane - Graphical scanner frontend for SANE)
 

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
Running 'sudo apt-get install --assume-yes libcupsimage2-dev'
Please wait, this may take several minutes...
error: Command failed. Re-try #1...
Running 'sudo apt-get install --assume-yes libcupsimage2-dev'
Please wait, this may take several minutes...
error: Command failed. Re-try #2...
Running 'sudo apt-get install --assume-yes libcupsimage2-dev'
Please wait, this may take several minutes...
error: Command failed. Re-try #3...
Running 'sudo apt-get install --assume-yes libcupsimage2-dev'
Please wait, this may take several minutes...
error: Package install command failed with error code 100
Would you like to retry installing the missing package(s) (y=yes*, n=no, q=quit) ? 

THE FINAL RESULT IS EXACTLY THE SAME.

mofa511@mofa511-TravelMate-X483:~$ cd /home/mofa511/Desktop
mofa511@mofa511-TravelMate-X483:~/Desktop$ sh hplip-3.14.10.run
Creating directory hplip-3.14.10
Verifying archive integrity... All good.
Uncompressing HPLIP 3.14.10 Self Extracting  Archive...........................................   ..................................................   ..................................................   ..................................................   ..................................................   ..................................................   ..................................................   ..................................................   ..................................................   ..................................................   ..................................................   ..................................................   ..................................................   ..................................................   ..................................................   ..................................................   ..................................................   ..................................................   ..................................................   ..................................................   ..................................................   ..................................................   ..................................................   ..................................................   ..................................................   ..................................................   ..................................................   ..................................................   ..................................................   ..................................................   ..................................................   ..................................................   ..................................................   ..................................................   ..................................................   ..................................................   ..................................................   ..................................................   ..................................................   ..................................................   ..................................................   ..................................................   ..................................................   ..................................................   ..................................................   ..................................................   ..................................................   ..................................................   ..................................................   ..................................................   ..................................................   ..................................................   ..................................................   ..................................................   ..................................................   ..................................................   ..................................................   ..................................................   ..............................................

HP Linux Imaging and Printing System (ver. 3.14.10)
HPLIP Installer ver. 5.1

Copyright (c) 2001-13 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

Installer log saved in: hplip-install_Fri-10-Oct-2014_04:53:02.log

\
note: Defaults for each question are maked with a '*'. Press <enter> to accept the default.
 

INSTALLATION MODE
-----------------
Automatic mode will install the full HPLIP solution with the most common options.
Custom mode allows you to choose installation options to fit specific requirements.

Please choose the installation mode (a=automatic*, c=custom, q=quit) : a

Initializing. Please wait...


INTRODUCTION
------------
This installer will install HPLIP version 3.14.10 on your computer.
Please close any running package management systems now (YaST, Adept, Synaptic, Up2date, etc).
 

DISTRO/OS CONFIRMATION
----------------------
Distro appears to be Ubuntu 14.04.

Is "Ubuntu 14.04" your correct distro/OS and version (y=yes*, n=no, q=quit) ? y


ENTER USER PASSWORD
-------------------
Please enter the sudoer (mofa511)'s password: 
 

INSTALLATION NOTES
------------------
Enable the universe/multiverse repositories. Also be sure you are using the Ubuntu "Main" Repositories. See: [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu) for more information.  Disable the CD-ROM/DVD source if you do not have the Ubuntu installation media inserted in the drive.

Please read the installation notes. Press <enter> to continue or 'q' to quit: 


RUNNING PRE-INSTALL COMMANDS
----------------------------
OK


INSTALL MISSING REQUIRED DEPENDENCIES
-------------------------------------
warning: There are 1 missing REQUIRED dependencies.
note: Installation of dependencies requires an active internet connection.
warning: Missing REQUIRED dependency: cups-image (CUPS image - CUPS image development files)


INSTALL MISSING OPTIONAL DEPENDENCIES
-------------------------------------
warning: There are 2 missing OPTIONAL dependencies.
note: Installation of dependencies requires an active internet connection.
warning: Missing REQUIRED dependency for option 'scan': sane-devel (SANE - Scanning library development files)
warning: Missing OPTIONAL dependency for option 'scan': xsane (xsane - Graphical scanner frontend for SANE)
 

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
Running 'sudo apt-get install --assume-yes libcupsimage2-dev'
Please wait, this may take several minutes...
error: Command failed. Re-try #1...
Running 'sudo apt-get install --assume-yes libcupsimage2-dev'
Please wait, this may take several minutes...
error: Command failed. Re-try #2...
Running 'sudo apt-get install --assume-yes libcupsimage2-dev'
Please wait, this may take several minutes...
error: Command failed. Re-try #3...
Running 'sudo apt-get install --assume-yes libcupsimage2-dev'
Please wait, this may take several minutes...
error: Package install command failed with error code 100
Would you like to retry installing the missing package(s) (y=yes*, n=no, q=quit) ? 

[]("https://launchpad.net/ubuntu/+archive/primary/+files/cups_1.7.2-0ubuntu1.1.debian.tar.gz")[URL="https://launchpad.net/ubuntu/+archive/primary/+files/cups_1.7.2-0ubuntu1.1.debian.tar.gz"]SO   I NOW HAVE A FAULTY SYSTEM, PERHAPS.  I NOW CANNOT USE THE PRINTER AT   ALL, EVER AGAIN.  I CANNOT UPDATE THE PRINTER DRIVER.  I AM GOING TO   QUIT UBUNTU.  BUT I DON'T SEE THE FAULT AS WITH UBUNTU, OR THE COMMUNITY   AT ALL.  I SEE THAT THIS IS THE FAULT OF THE THIRD PARTY SOFTWARE   PROVIDED - HEWLETT PACKARD - THAT THEY HAVE SLACKED OFF AND FAILED US,   PROBABLY FOR FINANCIAL REASONS.  The same can be said about acquiring a   Ubuntu PC WITH A GOOD WARRANTY outside the United States - it's   impossible.  Ubuntu will always be my favourite system, they just don't   have community support.  I have to go back to Microsoft - big hassle.    At least I'll have CLOUD.
```

[CENTER][IMG]http://ubuntuforums.org/images/smilies/smiley-faces-80.gif[/IMG]

If there's any further help, it would be greatly appreciated.[/CENTER]
[/URL][URL="https://launchpad.net/ubuntu/+archive/primary/+files/cups_1.7.2-0ubuntu1.1.debian.tar.gz"][CENTER]
[/CENTER]
[/URL]

---

### Post by christopher9 on 2014-10-10
In the terminal type the command:  sudo apt-get install -f  
Press [Enter]

What happens ?

---

### Post by skyesharica on 2014-10-11
> **christopher9 said:**
> In the terminal type the command:  sudo apt-get install -f  
Press [Enter]

What happens ?

I have now purged the hplip software.  I can't remember exactly what happened when I did this command but I definitely did it.  I recall always getting similar error messages.  It didn't work. ):P

---

### Post by Otto-C on 2014-10-13
Go to System Settings and click Printing
Locate your printer.
Remove/Delete printer in setup.
**
Go to Synaptic Package Manager if installed.
If not open a terminal and install.
Sudo apt-get install synaptic
enter password
enter "y' when asked
When done go to Synaptic Package Manager
or $ gksudo synaptic

If present there is a search box at top
enter and remove the following "hplip, hplip data, and
hplip cups". Locate them, to remove tick the green box
next to the item and click mark for complete removal,
then click apply and there may be a second click apply.
Do this for the items.
Power the printer off.
Power the computer off.
Wait 2 min.
**
Power up the computer.
Go to Synaptic Package Manager from the  search box at top
enter and install the following "hplip, hplip data, and
hplip cups". Locate them, to install tick the green box
next to the item and click mark for installation,
then click apply and click apply.
Do this for the items.
Power the computer off.
**
Power the printer on.
Power the computer on
*** See following screenshot to setup printer
*** [http://blog.sudobits.com/2012/04/13/how-to-install-printer-driver-on-ubuntu-12-04/](http://blog.sudobits.com/2012/04/13/how-to-install-printer-driver-on-ubuntu-12-04/)

Go to System Settings and click Printing
Click Add
Printer should be Auto Selected.
Click Forward
Tick Select Printer from DataBase
Select the one with Recommended
Click Forward
Choose the Driver. In most cases, default will be correct.
Click Forward
Describe printer and location (see its suggestions)
Click Apply
Click Close
**
Open Document file / Create New Document and enter some
test stuff and click Print.
**
If the above fails...
Open web browser and enter "localhost:631" this will be the
CUPS (Common Unix Printing System).
If not installed go to Synaptic Package Manager and search "cups"
and install from above directions. The re do "localhost:631".
Under "CUPS for Administrators" click "Adding Printers and Classes"
Click Add Printer
Click HP Printer
Follow the screen by accepting defaults.

[www.youtube.com/watch?v=pXiqmqVZnrY](www.youtube.com/watch?v=pXiqmqVZnrY)
cups starts @ 4:05

---

### Post by skyesharica on 2014-10-15
Thanks Otto-C,
Well, I've tried all of that, and here are some screen dumps.  It didn't work.  I still can't print.  I tried all twice and I think I got it down pat.  SO IT'S BACK HOME TO MICROSOFT.
Oh please have mercy on me and stop asking me to do things that don't work!
[ATTACH=CONFIG]257234[/ATTACH][ATTACH=CONFIG]257235[/ATTACH][ATTACH=CONFIG]257236[/ATTACH][ATTACH=CONFIG]257237[/ATTACH][ATTACH=CONFIG]257238[/ATTACH]

I HAVE MARKED THE PROBLEM AS SOLVED and SEEK $1K IN A MAD DASH ... ): ... IT IS HEWLETT PACKARD'S FAULT ... IT APPEARS AS UNFIXABLE ... FRIENDZ, DON'T BUY FROM THEM.  THIS SPARE UBUNTU LAPTOP WILL LAST 4 YEARS - I'D BET ON THAT.  I'LL HAVE 2 GET A DESKTOP.  Fans etc.  L@@K:

[http://ubuntuforums.org/showthread.php?t=2242381&page=3&p=13144769#post13144769](http://ubuntuforums.org/showthread.php?t=2242381&page=3&p=13144769#post13144769)

---

