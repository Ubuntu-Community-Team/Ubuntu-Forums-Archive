---
title: "Install 6.10 on laptop"
date: 2007-03-13
forum: Hardware &amp; Laptops
---

### Post by cfpole on 2007-03-13
I have an old Compaq laptop that I had Ubuntu 5.10 installed on.  It worked well.  I decided to upgrade to 6.10.  The hash on my download is correct.  I cut a disc and did a complete reload.  I have been trying to set the screen resolution, but have had no luck.  I had no trouble with 5.10, but have tried changing xorg.conf from both the root and terminal.  When I look at the setting in xorg, everything looks good, but when I try to change screen resolution from System > Preferences it won't allow anything except 640X480.  Also, how do I make sure that I have 6.10 installed?  When I go to 'About Ubuntu', I get a message that the module will not load.  If I look in help, it is headed Ubuntu 5.10.  How can I be sure that I have 6.10 loaded?

---

### Post by zvacet on 2007-03-13
system>administration>device manager>click advanced>scroll down and you will see your kernel version

---

### Post by cfpole on 2007-03-14
Thanks zvzcet:

When I look there I see: system>kernel.version          string  2.612-9-386

What is that telling me?

---

### Post by cfpole on 2007-03-15
Thought I would send my pertinent section of the xorg.conf file.  Perhaps it will help solve my resolution problem:

Section "Device"        Identifier      "S3 Inc. ViRGE/MX"
        Driver          "s3virge"
        BusID           "PCI:1:0:0"
        Option          "UseFBDev"              "true"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "S3 Inc. ViRGE/MX"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1400x1050" "1280x960" "1152x864" "1024x768"  "800x600" "640x480"   
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1400x1050" "1280x960" "1152x864" "1024x768"  "800x600" "640x480"          
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1400x1050" "1280x960" "1152x864" "1024x768"  "800x600" "640x480"               
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1400x1050" "1280x960" "1152x864" "1024x768"  "800x600" "640x480"        
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1400x1050" "1280x960" "1152x864" "1024x768"  "800x600" "640x480"       
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x960" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection


Thank you for looking at this,

Chuck

---

### Post by zvacet on 2007-03-16
It tell you that you don´t have Edgy installed,because Edgy kernel version is 2.6.17-11-generic.if you didn´t do it so far use alternate CD and 
```
sudo apt-cdrom add
```
```
sudo aptitude  dist-upgrade
```
P.S.you can not upgrade form Breezy to Edgy.So it is look like  breezy>dapper>edgy
Sorry for overlook

---

### Post by halw on 2007-03-16
Here is the link for upgrading to Dapper from Breezey --

[https://help.ubuntu.com/community/DapperUpgrades]("https://help.ubuntu.com/community/DapperUpgrades")

---

### Post by cfpole on 2007-03-16
Thanks for the info.  I do not have a broadband connection to the laptop.  Think I will go back to "Breezy" and leave it.  I may have to buy a new laptop.

Thanks again,

Chuck

---

