---
title: "Good New Ubuntu Friendly Scanner"
date: 2014-09-01
forum: Hardware
---

### Post by skyesharica on 2014-09-01
Hi Friends.  Well, when I got Ubuntu, I sold my hardware and got a new Printer/Scanner/Fax with third party software from Hewlett Packard.  I've updated to 14.04 and still find that SIMPLE SCAN never works.  It can't detect a scanner.  Now Gimp (popular art software) doesn't have the scanner option.  My drivers are up to date. 

What is the best software for detecting and using your scanner?

[ATTACH=CONFIG]256047[/ATTACH]

---

### Post by pqwoerituytrueiwoq on 2014-09-01
i made some web based software, *points at signature*
you could install xsane from the software center, the original front end that shipped ages ago but was replaced with simple scan by default
every linux GUI for scanners use the same back end (sane), for the most part HP is plug and play (the way it is impliede, not MS's definition)
if a hp scanner does not work update your hplip package

---

### Post by skyesharica on 2014-09-02
> **pqwoerituytrueiwoq said:**
> you could install xsane from the software center

for the most part HP is plug and play (the way it is impliede, not MS's definition)
if a hp scanner does not work update your hplip package

Wow - yer certainly sound like yer know what is here.  ):P  I'm downloading Xsane now.  I've reinstalled the HP driver but it doesn't work.  They don't guarantee their third party software.

> **pqwoerituytrueiwoq said:**
> for the most part HP is plug and play (the way it is impliede, not MS's definition)
if a hp scanner does not work update your hplip package

I've just tried XSane and it doesn't work.  Here is the typical error message.

[ATTACH=CONFIG]256074[/ATTACH]

I guess it is a fault with Hewlett Packard.  I'll just have to wait for them to fix it with the next hplip file.  What does "Plug & Play" mean?  The obvious?  Plug it in ... and it does stuff automatically?

---

### Post by pqwoerituytrueiwoq on 2014-09-02
try downgrading hplip, jsut grab the deb file from the previous release (12.04 or 13.10 i assume) and try it
[http://packages.ubuntu.com/search?keywords=hplip](http://packages.ubuntu.com/search?keywords=hplip)
install the deb with dpkg -i /path/to/file.deb
you can also try the driver from here
[http://hplipopensource.com/hplip-web/models/laserjet/hp_laserjet_professional_m1212nf_mfp.html](http://hplipopensource.com/hplip-web/models/laserjet/hp_laserjet_professional_m1212nf_mfp.html)
> **skyesharica said:**
> I guess it is a fault with Hewlett Packard.   I'll just have to wait for them to fix it with the next hplip file.   What does "Plug & Play" mean?  The obvious?  Plug it in ... and it  does stuff automatically?
with windows it is plug it in,grab a cd, do what it says to now it will play
with linux and HP in my recent experience
plug it in (while the computer is on), now play

---

### Post by skyesharica on 2014-09-03
> **pqwoerituytrueiwoq said:**
> try downgrading hplip, jsut grab the deb file from the previous release (12.04 or 13.10 i assume) and try it
[http://packages.ubuntu.com/search?keywords=hplip](http://packages.ubuntu.com/search?keywords=hplip)
install the deb with dpkg -i /path/to/file.deb
you can also try the driver from here
[http://hplipopensource.com/hplip-web/models/laserjet/hp_laserjet_professional_m1212nf_mfp.html](http://hplipopensource.com/hplip-web/models/laserjet/hp_laserjet_professional_m1212nf_mfp.html)

Thanks.  Tried it.  But got error messages - see image.  So I'll just wait for HP to fix it.

[ATTACH=CONFIG]256086[/ATTACH]

> **pqwoerituytrueiwoq said:**
> with windows it is plug it in,grab a cd, do what it says to now it will play
with linux and HP in my recent experience
plug it in (while the computer is on), now play

Thanks!  ;)

---

### Post by pqwoerituytrueiwoq on 2014-09-03
odd libcupsimage2-dev looks like it does not exist run
```
sudo apt-get update
sudo apt-get install libcupsimage2-dev
```
if that goes through try that again

---

### Post by skyesharica on 2014-09-03
> **pqwoerituytrueiwoq said:**
> odd libcupsimage2-dev looks like it does not exist run
```
sudo apt-get update
sudo apt-get install libcupsimage2-dev
```
if that goes through try that again
[B]
Did that.  Got this in terminal.:[/B]

mofa511@mofa511-TravelMate-X483:~$ sudo apt-get update
[sudo] password for mofa511: 
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty InRelease
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty Release.gpg    
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty Release        
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty/main amd64 Packages                   
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty/main i386 Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty/main Translation-en_AU
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty/main Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security InRelease
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release.gpg [933 B]
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release [59.7 kB]
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main amd64 Packages [135 kB]
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main i386 Packages [130 kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Translation-en
Fetched 326 kB in 5s (65.0 kB/s)
Reading package lists... Done
mofa511@mofa511-TravelMate-X483:~$ sudo apt-get install libcupsimage2-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libcupsimage2-dev : Depends: libcupsfilters-dev (>= 1.0~b1) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
mofa511@mofa511-TravelMate-X483:~$ 

**The scanner doesn't work.  How do I undo what I just did to my PC?**

> **pqwoerituytrueiwoq said:**
> odd libcupsimage2-dev looks like it does not exist run
```
sudo apt-get update
sudo apt-get install libcupsimage2-dev
```
if that goes through try that again

NOW NOTHING WORKS

Tried to reinstall the old file and got this mess.:

[ATTACH=CONFIG]256089[/ATTACH]

How do I manually install this dependency?

error: A required dependency 'cups-image (CUPS image - CUPS image development files)' is still missing.
error: Installation cannot continue without this dependency.
error: Please manually install this dependency and re-run this installer.

[B]I CAN NO LONGER INSTALL ANY DRIVER AT ALL - I JUST TRIED THE OLDER VERSION.  
I am a very sick person and this has caused me extreme distress.  I need the PC for food. PLEASE FIX THIS!!![/B]

---

### Post by sotiris2 on 2014-09-03
Try ```
sudo apt-get install -f
``` then try again ```
sudo apt-get install libcups2*
```

---

### Post by skyesharica on 2014-09-03
NO

I have just almost lost my printer.

Tell me how to get it back.  How do I wipe out what you just did to it.

Because I cannot install any driver at all now.

---

### Post by sotiris2 on 2014-09-03
It is the very first command I told you to enter. The first also in not actually specific to your printer (or printers in general) but a general command to try and get ubuntu to fix broken packages (which seems to be what's preventing you from installing any driver or probably any kind of software). Suit yourself anyways.

---

### Post by pqwoerituytrueiwoq on 2014-09-03
lets try to install the missing packages
```
sudo apt-get install -f
```

---

### Post by richard86 on 2014-09-04
You mention it is a printer/scanner/fax and that the scanner portion is not working but did not note if the printer portion is working.  If the printer is working and the scanner is not, you likely have run into the same problem I have.  First, assuming it is connected via USB, verify that the OS is seeing it by running lsusb, this will list all of the usb devices found.  For example, mine shows the following:

```
:~$ lsusbBus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 008: ID 03f0:2e12 Hewlett-Packard 
Bus 003 Device 009: ID 04c5:11f3 Fujitsu, Ltd 

```

If you see your device listed, then run sane-find-scanners.  It should find your scanner, and kick back something like:
```

found USB scanner (vendor=0x04c5, product=0x11f3) at libusb:001:002

```

If it doesn't find it, it maybe that you have to enable that device in the sane configuration files, or it may be that you are experiencing the same bug I am and even though it is a fully supported device, sane will not see it.

Hope that helps...Rich.

---

### Post by skyesharica on 2014-09-05
Thanks Rich, it does help.  I accept that the scanner doesn't work.  I have a printer that still works but because of the code I ran, I can never update the driver again.  Can you undo this code damage - mentioned above?  I learnt to completely avoid code unless someone very skilled takes you through it ... I don't just "try" some code.

> **pqwoerituytrueiwoq said:**
> lets try to install the missing packages
```
sudo apt-get install -f
```

Sorry if I was a bit rude.  I have been ill and confused.  I was angry with someone here about codes, and now I recall that I sent you a friend request!  Odd me?  I've calmed down and read the whole thread again.

So I tried the first command:  

sudo apt-get install -f 

[ATTACH=CONFIG]256202[/ATTACH]

Then I tried the second command.

sudo apt-get install libcups2*

A lot of this came up:  " ... already the newest version."
Then ...
Some packages could not be installed ...
Then ...
The following packages have unmet dependencies:
libcupsfilters-dev : Depends: libcupsfilters1 ... etc
Then ...
Unable to correct problems, you have held broken packages.

I tried to install an older version of the driver and got an error message that it wasn't supported by 14.04.
[ATTACH=CONFIG]256204[/ATTACH]

I tried to re-install my latest driver, in case it needed fixing, but got the same error message as always ... the same missing DEPENDENCY file.

[ATTACH=CONFIG]256203[/ATTACH] 
SO I GUESS IT IS THE FAULT OF HP.  My printer appears 2 b working.  Maybe an update will be possible and they will fix it??? ):P

---

### Post by pqwoerituytrueiwoq on 2014-09-10
maybe it will work if you grab the hplip deb from raring or saucy - [http://packages.ubuntu.com/search?keywords=hplip](http://packages.ubuntu.com/search?keywords=hplip)
trusty ships with 3.14.3, the latest is 3.14.6
maybe a upgrade will fix it

---

### Post by skyesharica on 2014-09-11
> **pqwoerituytrueiwoq said:**
> maybe it will work if you grab the hplip deb from raring or saucy - [http://packages.ubuntu.com/search?keywords=hplip](http://packages.ubuntu.com/search?keywords=hplip)
trusty ships with 3.14.3, the latest is 3.14.6
maybe a upgrade will fix it

Thanks.  I've had a look at the page.  I see the two versions you talk  of - Trusty updates and utopic.  But can you please explain to me what  these are?  How do they differ from the Hewlett Packard updates?  

I have the latest driver but I can't update it again.  I'm not sure if this is due to the code I ran here, or if it is a fault with HP software.

---

### Post by pqwoerituytrueiwoq on 2014-09-11
Comment:
do you have [synaptic](apt:synaptic) installed? that will help, it is a very nice gui for package management
when you install with a deb you don't end up with issues like this (unless you install with dpkg -i /path/to/file.deb)

Where we are:
1st thing we need to do is undo the damage caused by what was done earlier, clearly we can't fix it by installing more stuff, so plan b is remove it
i suggest purging hplip (apt-get purge hplip), if it will let you then apt-get autoremove

What do do later:
then install the deb file for hplip
If you install [gdebi](apt:gdebi), i prefer that for installing a deb over the software center

---

### Post by skyesharica on 2014-09-13
> **pqwoerituytrueiwoq said:**
> 
Where we are:
1st thing we need to do is undo the damage caused by what was done earlier, clearly we can't fix it by installing more stuff, so plan b is remove it
i suggest purging hplip (apt-get purge hplip), if it will let you then apt-get autoremove


That sounds great.  But you say "i suggest" and "if it will let you".  So I may end up with a worse mess.  It's all very advanced stuff too.  At the moment my printer works.  I've accepted that I probably won't ever be able to upload another driver for it ... until I do the next clean install of Ubuntu in two years.  :mad:

---

### Post by pqwoerituytrueiwoq on 2014-09-13
but if you still have broken packages you cant install ANYTHING no even updates

---

### Post by skyesharica on 2014-09-13
> **pqwoerituytrueiwoq said:**
> but if you still have broken packages you cant install ANYTHING no even updates

Yes, I understand that.  It can't be updated until the system is wiped.  But I don't want to experiment with code etc - because that appears to be what has gone wrong in the first place.

---

### Post by pqwoerituytrueiwoq on 2014-09-13
if you stick with debs it will tell you if it will break stuff installing it and not let you easily install it, so pulling a deb from utopic may work, if not it will not install

---

### Post by Sef on 2014-09-14
What is your printer model?  Have you looked at the [HP page]("http://hplipopensource.com/hplip-web/supported_devices/index.html")?

---

### Post by skyesharica on 2014-09-20
Thanks Sef, I'VE DONE ALL THE BASICS.  And now people are answering the  other thread I made about the same problem .......... [http://ubuntuforums.org/showthread.php?t=2242660]("http://ubuntuforums.org/showthread.php?t=2242660%29--just") .......... just realised I didn't hit  subscribe.  I've got so much on - and it's such a learning curve ... but I  see the ray of light.  OMG I thought it was time to re-invest in <snip> MS.  I've lost so much cash on all of the SOFTWARE and HARDWARE  ... and am such a small fish that[SIZE=5]**[COLOR=#ee82ee] life is now but a silly dream[/COLOR]**[/SIZE].  :popcorn:

---

### Post by skyesharica on 2014-10-10
Hi [[IMG]http://ubuntuforums.org/customavatars/avatar865458_5.gif[/IMG] ]("http://ubuntuforums.org/member.php?u=865458")[**[COLOR=#000000]pqwoerituytrueiwoq[/COLOR]**]("http://ubuntuforums.org/member.php?u=865458") and [**[COLOR=#000000]sotiris2[/COLOR]**]("http://ubuntuforums.org/member.php?u=1845661") and [**[COLOR=#000000]richard86[/COLOR]**]("http://ubuntuforums.org/member.php?u=1943503") and [ [IMG]http://ubuntuforums.org/customavatars/avatar57646_21.gif[/IMG]]("http://ubuntuforums.org/member.php?u=57646")[**[COLOR=#C61919][B]Sef**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=57646")

My apologies for not answering sooner.  I've been very ill and unable to respond.  It looks like a disaster.

Firstly, yes, Rich, it appears that the scanner function is simply not working now.  So that is Hewlett Packard's fault.  

Then, it appears that I stuffed the software by trying to install a previous version ... older versions are available at the website ... so this is Hewlett Packard's fault again.  This is when I got the error message about the missing dependency:  libcupsimage2-dev.  I've never had that error before, so it is a fault with the driver software ... perhaps it is not up to date with Ubuntu 14.04 LTS.

Then, I tried all the tips--which I assume were most kindly given.  Like: sudo apt-get update ... sudo apt-get install libcupsimage2-dev.  And:  sudo apt-get install -f ... sudo apt-get install libcups2*.  No matter what I tried, I always got similar screens to these - about the missing dependency and two missing optional dependencies for scanning.  Then the mess up continues with further screens about broken up software.

[ATTACH=CONFIG]257095[/ATTACH]
[ATTACH=CONFIG]257096[/ATTACH]
[ATTACH=CONFIG]257098[/ATTACH]
[ATTACH=CONFIG]257100[/ATTACH]

I've since been sent an upgrade notice for hplip 3.14.10 and it still doesn't work ... same error messages.

Then I tried to clean up the damage done, as you were right, my general updates were affected.  I thought it was better to keep a good Ubuntu than a bad printer.  My updates started requesting "partial" etc.  So I decided you were right - [**[COLOR=#000000]pqwoerituytrueiwoq[/COLOR]**]("http://ubuntuforums.org/member.php?u=865458") when you said: ** "**but if you still have broken packages you cant install ANYTHING no even updates".  So I did the PURGE command:  sudo apt-get purge hplip*.  This is the copy of the terminal.:

[COLOR=#0000cd]mofa511@mofa511-TravelMate-X483:~$ sudo apt-get purge hplip*
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
mofa511@mofa511-TravelMate-X483:~$ [/COLOR]

AND YES, IT DID WORK ... I NOW HAVE NO PRINTER ... I AM PURGED OF DRIVER SOFTWARE.

I tried to install the CUPS whatever:  
**[SIZE=3]“cups” 1.7.2-0ubuntu1.1 source package in Ubuntu[/SIZE]**

I was told I needed the version with the word "deb" in it.  So I got this one.:

[cups_1.7.2-0ubuntu1.1.debian.tar.gz]("https://launchpad.net/ubuntu/+archive/primary/+files/cups_1.7.2-0ubuntu1.1.debian.tar.gz")

It didn't work.  I downloaded the GDebi software and tried to open it but it said:  "not a Debian package".  (Hey, I don't even know what Debian means.)  See below.

[ATTACH=CONFIG]257102[/ATTACH]

Thank heavens though - PERHAPS - my software is no longer faulty.  I still have a missing dependency but I don't get the UPDATER error message of REQUIRING A PARTIAL UPGRADE (due to software problems).  I get all the updates.  I looked closely - and saw some of the updates had the word "image", like "linux-image-extra-3.13.0.37-generic".  But it made no difference.  

I then tried to install the latest driver again.  But it made no difference.  It had the same error message:  "Missing REQUIRED dependency: cups-image (CUPS image - CUPS image development files)".  I don't know if this means that my regular software updates will be affected in future.  Here is a copy of the Terminal commands.:

[COLOR=#0000cd]mofa511@mofa511-TravelMate-X483:~$ cd /home/mofa511/Desktop
mofa511@mofa511-TravelMate-X483:~/Desktop$ sh hplip-3.14.10.run
Creating directory hplip-3.14.10
Verifying archive integrity... All good.
Uncompressing HPLIP 3.14.10 Self Extracting Archive...........................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................

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
Would you like to retry installing the missing package(s) (y=yes*, n=no, q=quit) ? [/COLOR]
[B]
THE FINAL RESULT IS EXACTLY THE SAME.[/B]

[COLOR=#0000cd]mofa511@mofa511-TravelMate-X483:~$ cd /home/mofa511/Desktop
mofa511@mofa511-TravelMate-X483:~/Desktop$ sh hplip-3.14.10.run
Creating directory hplip-3.14.10
Verifying archive integrity... All good.
Uncompressing HPLIP 3.14.10 Self Extracting Archive...........................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................

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
Would you like to retry installing the missing package(s) (y=yes*, n=no, q=quit) ? [/COLOR]

[TABLE="class: narrow listing"]
[TR]
[TD][URL="https://launchpad.net/ubuntu/+archive/primary/+files/cups_1.7.2-0ubuntu1.1.debian.tar.gz"][SIZE=3][COLOR=#ff8c00][FONT=century gothic][B][URL="https://launchpad.net/ubuntu/+archive/primary/+files/cups_1.7.2-0ubuntu1.1.debian.tar.gz"][SIZE=3][COLOR=#ff8c00][FONT=century gothic][B]SO  I NOW HAVE A FAULTY SYSTEM, PERHAPS.  I NOW CANNOT USE THE PRINTER AT  ALL, EVER AGAIN.  I CANNOT UPDATE THE PRINTER DRIVER.  I AM GOING TO  QUIT UBUNTU.  BUT I DON'T SEE THE FAULT AS WITH UBUNTU, OR THE COMMUNITY  AT ALL.  I SEE THAT THIS IS THE FAULT OF THE THIRD PARTY SOFTWARE  PROVIDED - HEWLETT PACKARD - THAT THEY HAVE SLACKED OFF AND FAILED US,  PROBABLY FOR FINANCIAL REASONS.  The same can be said about acquiring a  Ubuntu PC WITH A GOOD WARRANTY outside the United States - it's  impossible.  Ubuntu will always be my favourite system, they just don't  have community support.  I have to go back to Microsoft - big hassle.   At least I'll have CLOUD.

[/B][/FONT][/COLOR][/SIZE][CENTER]):P

If there's any further help, it would be greatly appreciated.[/CENTER]
[/URL][URL="https://launchpad.net/ubuntu/+archive/primary/+files/cups_1.7.2-0ubuntu1.1.debian.tar.gz"][CENTER]
[/CENTER]
[/URL][/B][/FONT][/COLOR][/SIZE]



[/URL][/TD]
[/TR]
[/TABLE]

---

### Post by richard86 on 2014-10-10
Regarding package dependency issues, [http://askubuntu.com/questions/140246/how-do-i-resolve-unmet-dependencies](http://askubuntu.com/questions/140246/how-do-i-resolve-unmet-dependencies) has some good information about cleaning that up.  > sudo apt-get clean might be your friend.  Looking through the thread, I didn't notice where you ever identified the model of the printer...can you provide that?  Regarding some other items you had posted, Debian is a Linux distribution which Ubuntu is based upon.  Regarding Ubuntu support, if you buy a PC from someone like ZaReason or System76, you'll get support.  And you can get support directly from Canonical for around $100 per year...check out [http://www.ubuntu.com/management/ubuntu-advantage](http://www.ubuntu.com/management/ubuntu-advantage)

---

### Post by skyesharica on 2014-10-15
> **richard86 said:**
> Looking through the thread, I didn't notice where you ever identified the model of the printer...can you provide that?

HP LaserJet Pro M1212nf Multifunction Printer 
> **richard86 said:**
> Regarding package dependency issues, [http://askubuntu.com/questions/140246/how-do-i-resolve-unmet-dependencies](http://askubuntu.com/questions/140246/how-do-i-resolve-unmet-dependencies) has some good information about cleaning that up.   might be your friend.  

G'day friend.  But friends don't give each other these sorts of run arounds when there's a lot of money on the table - AND ILL HEALTH.  I've had a look at the article.  Thanks, it looks great.  But I feel that I may just complicate the problem ... It starts off with some simple solutions, similar to the purge command, but then it keeps saying stuff like "if that doesn't work" etc ... or even:  "Delete the held packages one by one, running dist-upgrade each time, until there are no more held packages."  I wouldn't have a clue about advanced stuff like that--or any programming--and could end up in a worse mess.  I now have proper updates and I'd like to keep the working PC.

> **richard86 said:**
> Debian is a Linux distribution which Ubuntu is based upon.

Thankyou - and again, it shows how important it is for non-specialists to leave this scene.  If you look at my pop up error message FOR INSTALLING THE MISSING DEPENCY (CUPS ETC), it says " ... is not a Debian package" ... VERY ODD AND CONFUSING AND ONLY FOR EXPERTS.

> **richard86 said:**
> Regarding Ubuntu support, if you buy a PC from someone like ZaReason  or System76, you'll get support.  And you can get support directly from  Canonical for around $100 per year...check out [http://www.ubuntu.com/management/ubuntu-advantage](http://www.ubuntu.com/management/ubuntu-advantage)

I may get support but an overseas warranty is nearly impossible.  Thanks for that, however, as you can see, the support can go on FOREVER, if the third party software developer (PRINTER SOFTWARE) lets people down.  It is the fault of Hewlett Packard.  And I must return to Microsoft.  I will hang onto my Ubuntu, forever, however, and keep it as a spare, and I hope that one day people will pay it proper respect ... so that it can be popularly supported.

---

### Post by skyesharica on 2014-10-16
> **Sef said:**
> What is your printer model?

[COLOR=#000080][SIZE=3][FONT=lucida console]I love all the poems up to "Wanting" - and then I had to knock off reading stuff.

Friend & Ubuntu Moderator, I read your beautiful poem entitled "My Friends".  Do you have the right job?  [/FONT][/SIZE][/COLOR][COLOR=#000080][SIZE=3][FONT=lucida console][COLOR=#000080][SIZE=3][FONT=lucida console]<i'm just a 'will robinson' feedback loop 2 u =D>  [/FONT][/SIZE][/COLOR]Look these people are all geniuses.  Below is an image of my brain score ... but hey, in a way it's getting worse, it gets better on Ubuntu dayz ... but they are FAR TOO HARD 4 ME.  I don't think it's your intellect but your LACK OF FUN.  Once I was an artist.  I inheritied a gift but it wasn't "Andy Warhol" and so - well, you know the story of "no cash/down".  Do you have cash?  But the darkness and lonliness never became my friend - I just had to quit.  I'm trying business now. 

DO NOT BUY HEWLETT PACKARD.  I'M NOT A MODERATOR, OR A PROGRAMMER, OR A GENIUS OF ANY KIND AT ALL ... I'M A USER WHO DID THIS TROUBLE SHOOTING (PERIPHERAL > PRINTER/FAX/SCAN) TASK.  I consider it is the fault of Hewlett Packard.  Maybe you can work that out for sure.  I think you should black list them.  I thought to send admin an email but it would be seen as spam ... too lengthy.  I'll go back to Ubuntu when they've set up a safe list of hardware suppliers, and there's warranties outside of the States ... hey, I think it might be the hardware more now, because the new version came on time - a clean install is all people need.  Try calling the wonderful Secretary who phoned:  "the "Backup Girl" - it's a Carrie Fisher/Sarah Jessica Parker joke from the TV series "_Sex and the City_" - she will love you for it, and try some backup too.  Cloud - OMG NO!  Is that right?  Is it not so kewl a thing--insecure or whatever?  Anyway, don't answer, as I've had it--I'm actually on a medication that makes me speedy tonight.  It's bad stuff.  I need rest.  To continue I will NEVER buy from Hewlett Packard, anything at all, again.  NEVER ... because Ubuntu are my FRIENDZ ... FRIENDZ ARE EVERYTHING 2 ME.  AND I BELIEVE THEY ***ARE DEFINITELY NOT*** UBUNTU FRIENDLY.  YOUR SILENCE WILL SOMEHOW PROVE THAT 2 ME ... I ask Jesus.  At the moment, I am very down with illness and friendz r mi GREATEST GIFT, if you get the flow of that.  Lonliness ... well a good movie helps a lot.   :D  

I've decided Bill Gates is a "kitten nerd" more than a "Monstrous Nerd" who has had extreme ill luck with a woman.  Or all of them.  So I don't mind investing in Microsoft again.  But it's some serious serious cash for a battler, a sorta "biz starter".  A sick woman.  Hell!

So I wave my hand now to the genius folks - PLEASE PLEASE PLEASE don't post ANYTHING unless you've got the absolute fix for that printer ... I can't read anymore, I'm sick.  I try 2 hard.

Have good luck with women.  Don't get a witch.  And HAVE FUN.  

AND          **********CASH**********          more than 10, friend.

I am not used to that - EITHER -
to someone taking care of me.

):P](*,)#-o=;:-({|=\\:D/[INDENT]P.S.  [ATTACH=CONFIG]257266[/ATTACH]
[/INDENT]
[CENTER][ATTACH=CONFIG]257265[/ATTACH]
[/CENTER]


[/FONT][/SIZE][/COLOR]

---

