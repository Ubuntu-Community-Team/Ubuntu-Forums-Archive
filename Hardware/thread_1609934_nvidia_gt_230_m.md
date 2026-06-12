---
title: "nvidia gt 230 m"
date: 2010-10-31
forum: Hardware
---

### Post by akshatverma73 on 2010-10-31
salutations ppl!

i have a hp pavilion dv6 2164tx
4gb ram
***1gb nvidia gt 230m graphic card,
seagate 500gb harddrive



ubuntu installed all fine but i'm experiencing certain problems.....

1. when i booted up for the first time i the screen blacked out and i had to hard reset my laptop to make it work again
i installed my nvidia graphics driver as predefined by 'additional drives' menu
when i enable it and restart my resolution moves down from 1366x768 to 640x480 pixels


2.whenever i install or remove a program i get an error message"
  


***installArchives() failed: perl: warning: Setting locale failed. 
perl: warning: Please check that your locale settings: 
    LANGUAGE = (unset), 
    LC_ALL = (unset), 
    LANG = "en_IN.ISO8859-1" 
    are supported and installed on your system. 
perl: warning: Falling back to the standard locale ("C"). 
locale: Cannot set LC_CTYPE to default locale: No such file or directory 
locale: Cannot set LC_MESSAGES to default locale: No such file or directory 
locale: Cannot set LC_ALL to default locale: No such file or directory 
perl: warning: Setting locale failed. 
perl: warning: Please check that your locale settings: 
    LANGUAGE = (unset), 
    LC_ALL = (unset), 
    LANG = "en_IN.ISO8859-1" 
    are supported and installed on your system. 
perl: warning: Falling back to the standard locale ("C"). 
locale: Cannot set LC_CTYPE to default locale: No such file or directory 
locale: Cannot set LC_MESSAGES to default locale: No such file or directory 
locale: Cannot set LC_ALL to default locale: No such file or directory 
Selecting previously deselected package ddccontrol-db. 
(Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 128078 files and directories currently installed.) 
Unpacking ddccontrol-db (from .../ddccontrol-db_20061014-4_all.deb) ... 
Selecting previously deselected package libddccontrol0. 
Unpacking libddccontrol0 (from .../libddccontrol0_0.4.2-6ubuntu1_i386.deb) ... 
Selecting previously deselected package ddccontrol. 
Unpacking ddccontrol (from .../ddccontrol_0.4.2-6ubuntu1_i386.deb) ... 
Selecting previously deselected package gddccontrol. 
Unpacking gddccontrol (from .../gddccontrol_0.4.2-6ubuntu1_i386.deb) ... 
Processing triggers for man-db ... 
perl: warning: Setting locale failed. 
perl: warning: Please check that your locale settings: 
    LANGUAGE = (unset), 
    LC_ALL = (unset), 
    LANG = "en_IN.ISO8859-1" 
    are supported and installed on your system. 
perl: warning: Falling back to the standard locale ("C"). 
locale: Cannot set LC_CTYPE to default locale: No such file or directory 
locale: Cannot set LC_MESSAGES to default locale: No such file or directory 
locale: Cannot set LC_ALL to default locale: No such file or directory 
perl: warning: Setting locale failed. 
perl: warning: Please check that your locale settings: 
    LANGUAGE = (unset), 
    LC_ALL = (unset), 
    LANG = "en_IN.ISO8859-1" 
    are supported and installed on your system. 
perl: warning: Falling back to the standard locale ("C"). 
/usr/bin/mandb: can't set the locale; make sure $LC_* and $LANG are correct 
Processing triggers for doc-base ... 
perl: warning: Setting locale failed. 
perl: warning: Please check that your locale settings: 
    LANGUAGE = (unset), 
    LC_ALL = (unset), 
    LANG = "en_IN.ISO8859-1" 
    are supported and installed on your system. 
perl: warning: Falling back to the standard locale ("C"). 
Processing 1 added doc-base file(s)... 
Registering documents with scrollkeeper... 
Processing triggers for menu ... 
Processing triggers for desktop-file-utils ... 
Processing triggers for python-gmenu ... 
locale: Cannot set LC_CTYPE to default locale: No such file or directory 
locale: Cannot set LC_MESSAGES to default locale: No such file or directory 
locale: Cannot set LC_ALL to default locale: No such file or directory 
Rebuilding /usr/share/applications/desktop.en_IN.ISO8859-1.cache... 
WARNING: System locale is invalid 
Processing triggers for python-support ... 
Setting up firmware-b43-installer (4.150.10.5-4) ... 
Not supported low-power chip with PCI id 14e4:4315! 
Aborting. 
dpkg: error processing firmware-b43-installer (--configure): 
 subprocess installed post-installation script returned error exit status 1 
Setting up ddccontrol-db (20061014-4) ... 
Setting up libddccontrol0 (0.4.2-6ubuntu1) ... 
Setting up ddccontrol (0.4.2-6ubuntu1) ... 
Setting up gddccontrol (0.4.2-6ubuntu1) ... 
Processing triggers for libc-bin ... 
ldconfig deferred processing now taking place 
Processing triggers for menu ... 
Errors were encountered while processing: 
 firmware-b43-installer 
Setting up firmware-b43-installer (4.150.10.5-4) ... 
Not supported low-power chip with PCI id 14e4:4315! 
Aborting. 
dpkg: error processing firmware-b43-installer (--configure): 
 subprocess installed post-installation script returned error exit status 1 
***


i need some assistance.....thank you

---

### Post by P4man on 2010-10-31
About the first (driver) issue, when you go to system | administration | additional drivers you will probably see 3 different drivers for your nvidia card. Make sure you select the "current" / recommended version, not the older legacy ones.

I suspect the other problem is somehow related, but I have no idea how. If installing the correct drivers doesnt fix it, try this. Open a terminal (applications accessories terminal) and paste this command:

```
sudo dpkg-reconfigure localeconf 
```

type your password when prompted.

---

### Post by akshatverma73 on 2010-10-31
> **P4man said:**
> About the first (driver) issue, when you go to system | administration | additional drivers you will probably see 3 different drivers for your nvidia card. Make sure you select the "current" / recommended version, not the older legacy ones.

I suspect the other problem is somehow related, but I have no idea how. If installing the correct drivers doesnt fix it, try this. Open a terminal (applications accessories terminal) and paste this command:

```
sudo dpkg-reconfigure localeconf 
```type your password when prompted.


this is what i got by typing the sudo code.....

Package `localeconf' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: localeconf is not installed



and the i'm using the "current" version for the nvidia drivers

---

### Post by P4man on 2010-10-31
Turns out in newer ubuntu's that should be

```
sudo dpkg-reconfigure locales
```

But Im doubtful that will solve a whole lot.
As for the nvidia driver issue..  maybe you are having the bug described here:

[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/660596?comments=all](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/660596?comments=all)

That page also contains some possible solutions.

---

### Post by akshatverma73 on 2010-11-03
> **P4man said:**
> Turns out in newer ubuntu's that should be

```
sudo dpkg-reconfigure locales
```But Im doubtful that will solve a whole lot.
As for the nvidia driver issue..  maybe you are having the bug described here:

[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/660596?comments=all](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/660596?comments=all)

That page also contains some possible solutions.






Here we go:
 A) Go to the Synaptics Package Manager, do a search for NVIDIA and remove everything.
 B) Download NVIDIA-Linux-x86-256.53.run from the NVIDIA Linux website and save it somewhere
 C) Open up a terminal and type
Code:
 /etc/init.d/gdm stop
 D) now type
Code:
 sudo bash
 E) then navigate to the folder where you saved your NVIDIA driver
 F) Type
Code:
  ./NVIDIA-Linux-x86-256.53.run
 G) Click yes to everything
 H) restart and boot up in safe mode (hit shift after bios)
 I)edit your Xorg .conf file by opening up a terminal and typing
Code:
 sudo gedit /etc/X11/xorg.conf
 J) If you like remove everything in it and paste in the following  (you may have to change the customedid path and also your busID) and  save:
Code:
 Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    Option  "ConnectedMonitor"  "DFP-0"
    Option  "CustomEDID"         "DFP-0:/etc/X11/nvidiaedid.bin"
    BusID "PCI:1:0:0"
EndSection
 K) open the terminal again and type:
Code:
 sudo gedit /etc/default/grub/
 and change the line to the following: GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"
 L) Now often when restarting every is faced with the no screens  problem, I think this is due to nouveau being a pain, so open up your  terminal again and type
Code:
 sudo gedit /etc/modprobe.d/blacklist.conf
 and in this file at the bottom add the following
Code:
 blacklist nouveau










i tried using the steps given above but when i try to install the nvidia*.run file its says permission denied

---

### Post by P4man on 2010-11-03
make the nvidia driver executable before running it

```
chmod a+x NVIDIA-Linux-*
```

And note everything is case sensitive.

---

### Post by DroTTo on 2010-11-06
Hi, my english is very bad, so:

I had the same problem:
"Setting up firmware-b43-installer (4.150.10.5-4) ...
Not supported low-power chip with PCI id 14e4:4315!
Aborting.
dpkg: error processing firmware-b43-installer (--configure):
subprocess installed post-installation script returned error exit status 1 "

Now i solved it by activating the b43 driver from the panel additional driver.

(Sorry i'm italian and my ubuntu is in this language.)
Hopefully solve too!
Angel!

---

### Post by akshatverma73 on 2010-11-07
> **P4man said:**
> make the nvidia driver executable before running it

```
chmod a+x NVIDIA-Linux-*
```And note everything is case sensitive.





did it but the terminal doesn't state any progress
after typing the code in the terminal , i do not get any indication weather the the file made executable
 

neways i tried running the package again and i get the same error message

---

### Post by P4man on 2010-11-07
> **akshatverma73 said:**
> 

neways i tried running the package again and i get the same error message

Which error was that?
BTW, chmod doesnt give any output unless there is an error, so thats okay.

---

### Post by akshatverma73 on 2010-11-11
> **P4man said:**
> Which error was that?
BTW, chmod doesnt give any output unless there is an error, so thats okay.



well when i use the code "chmod a+x...."
it said permission denied\

well as what i can perceive is that the code " /etc/stop gdm" was not working so i changed(by googling it) it to sudo stop gdm,
when i do that my computer takes me to the start up screen(the one with ubuntu logo and progress bar,with only 2 out 5 circles filled)
 and gets stuck........

any advice?

---

### Post by P4man on 2010-11-11
You have to put sudo in front of that chmod command as well. sudo makes you execute a command with root (administrator) permissions.

---

### Post by akshatverma73 on 2010-11-11
> **P4man said:**
> You have to put sudo in front of that chmod command as well. sudo makes you execute a command with root (administrator) permissions.

didn't knew that..... sorry for my  stupidity

---

### Post by P4man on 2010-11-11
There is nothing stupid about not knowing. I should have said so, but I thought you were doing this form a root prompt in recovery mode.

---

### Post by akshatverma73 on 2010-11-11
> **P4man said:**
> There is nothing stupid about not knowing. I should have said so, but I thought you were doing this form a root prompt in recovery mode.




 on typing this code "/media/*/Documents/Nvidia/driver.run"   i get an error permission denied



or else 

        ERROR: You appear to be running an X server; please exit X before            
         installing.  For further details, please see the section INSTALLING   
         THE NVIDIA DRIVER in the README available on the Linux driver      

how to exit the x server?
the readme isn't that clear   
         download page at [www.nvidia.com]("http://www.nvidia.com").


also   sudo gdm stop
[sudo] password for akshat: 

** (gdm-binary:2233): WARNING **: Failed to acquire org.gnome.DisplayManager

** (gdm-binary:2233): WARNING **: Could not acquire name; bailing out

---

### Post by P4man on 2010-11-11
to stop gnome:

```
sudo service gdm stop
```

I have to admit Im losing sight of whats going on exactly now.

---

### Post by akshatverma73 on 2010-11-11
> **P4man said:**
> to stop gnome:

```
sudo service gdm stop
```I have to admit Im losing sight of whats going on exactly now.




can u just tell me how to exit x as mention in my previous post?

---

### Post by P4man on 2010-11-11
That command does stop X

```
sudo service gdm stop
```
If it fails, then X probably isnt running. But you can also try

```
sudo init 1
```

---

### Post by akshatverma73 on 2010-11-13
IT Worked!!!!


well as a last resort i reinstalled my ubuntu 10.10, updated my packages,installed the additional drivers (nvidia current) and vola!  everythin is workin! the resolution is 1366x768 with the "extra graphics" appearance 

thanks a lot for ur support!\\:D/

---

