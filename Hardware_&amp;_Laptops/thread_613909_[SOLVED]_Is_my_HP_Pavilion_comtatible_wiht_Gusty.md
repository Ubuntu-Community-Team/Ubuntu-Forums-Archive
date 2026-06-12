---
title: "[SOLVED] Is my HP Pavilion comtatible wiht Gusty?"
date: 2007-11-15
forum: Hardware &amp; Laptops
---

### Post by Newbie1978 on 2007-11-15
Hello! I recently purchase this Laptop and I was wondering if it is compatible with Ubuntu 7.10 Gusty gibbon, in my old laptop I have Ubuntu ultimate 1.4 (Ubuntu version 7.04) running relatively smoothly, some problems but nothing mayor completely fixable, but since the new one is so much better than the last one and since the new version of Ubuntu is out, I would like to know if there is somebody out there with the same laptop that can tell me if the hardware is compatible for Gusty, or better yet if you think is worth it to upgrade from Feisty to Gusty, for what I understand there is people completely behind this distro and others no so much, In my opinion the problem relate to your specific hardware if your hardware can handle Gusty you like it but if your hardware can't handle it you will hate it, please help me decide between Gusty or Feisty 

HP Pavilion Entertainment-center notebook PC
64-bit 1.9 GHz AMD Turion 64 X2 TL-58 processor, 250 GB hard drive, 2 GB RAM
Nvidia GeForce Go 7150 graphics
Running on dual boot Windows Vista Home Premium and Ubuntu ultimate 1.4

---

### Post by staticvoid on 2007-11-15
Yo!
I have the same laptop. I popped in the live cd and it look like THE WIRELESS does not work. Broadcom. Nvidia obviously will need an extra driver (ubuntu should download that, i never saw if it worked, because I was not connected to the net)

It runs VERY smoothly off the live cd :D. faster then my 512 mb ram 1 ghz VAIO for sure :)

I'd say go for the Gutsy Gibbon and figure out the bugs. its worth it :D Stay on the cutting edge.

sv

p.s. the quick play even works!! :D

---

### Post by Newbie1978 on 2007-11-15
Awsome!!!! thanks for the 411 on that, since I already download the Ubuntu ultimate 1.6 which runs on Ubuntu 7.10 Gusty version, I will give this a try :)

---

### Post by Newbie1978 on 2007-11-20
Yesterday I sadly found that my bran new HP laptop is not compatible with Ubuntu 7.4 or the newer 7.10 (hardware issues) so now I will have to research for a way to make it work, some people say thats the fun part of Linux, but for me that was a pain in the @#~! because when I give up trying to load the live DVD, and try to get back in Windows to look for some info about this issue, much for my surprise Windows does not stared automatically, (some star up error) this is quite common in Windows, the worst  part was that I end up re installing form partition because none of the others solution work, good thing that I back up all the time so I did not lose anything, if any one can help me about this issue I will appreciate. Thank you

---

### Post by Newbie1978 on 2007-11-21
Well after a lot of frustration I discover that my new laptop don't work with Linux (hardware issues) this are my specs HP Pavilion Entertainment-center notebook PC DV6660se 64-bit 1.9 GHz AMD Turion 64 X2 TL-58 processor, 250 GB hard drive, 2 GB RAM Nvidia GeForce Go 7150 graphics if anyone manage to install a Linux distro in this model please help me

---

### Post by Ikslewap on 2007-11-21
I use Solaris 10 more than I do Ubuntu.  However, I may be able to shed a little light on your situation.  Sadly, the system isn't going to install properly because of your processor.  Those who have posted on this forum have been using x64 systems.  Your AMD Turion 64 is likely the culprit.  Ubuntu has an x64 release. When downloading the distro have you made certain to select that you have an x64 system and not the typical x86?  There is an option on ubuntu.com.  However, the standard install is for x86 architecture (Pentiums, 32 bit AMDs).  MOST Linux distros have an x64 architecture release and Ubuntu is no exception.  if you are choosing the x64 option then you should be able to install.  I have an older Pavilion (ZD8000) and Ubuntu runs smoother than a clean XP install.  As long as you are certain that you are choosing x64 then you may have another problem.  

-Are you able to install at all?  
-What kind of error message are you getting?  

If you can supply this information I may be able to help more.  Wireless drivers on Pavilions is a challenge for Linux, but I can help you in this regard as well if you get this puppy running.

-Paws

---

### Post by Newbie1978 on 2007-11-22
> **Ikslewap said:**
> I use Solaris 10 more than I do Ubuntu.  However, I may be able to shed a little light on your situation.  Sadly, the system isn't going to install properly because of your processor.  Those who have posted on this forum have been using x64 systems.  Your AMD Turion 64 is likely the culprit.  Ubuntu has an x64 release. When downloading the distro have you made certain to select that you have an x64 system and not the typical x86?  There is an option on ubuntu.com.  However, the standard install is for x86 architecture (Pentiums, 32 bit AMDs).  MOST Linux distros have an x64 architecture release and Ubuntu is no exception.  if you are choosing the x64 option then you should be able to install.  I have an older Pavilion (ZD8000) and Ubuntu runs smoother than a clean XP install.  As long as you are certain that you are choosing x64 then you may have another problem.  

-Are you able to install at all?  
-What kind of error message are you getting?  

If you can supply this information I may be able to help more.  Wireless drivers on Pavilions is a challenge for Linux, but I can help you in this regard as well if you get this puppy running.

-Paws

Hello! I only try once to install Ubuntu ultimate 1.4 which I believe is base on Ubuntu feisty 7.04, the results where horrible not only the live dvd never load even when I try with "noapic" (which works fine in my other laptop an HP pavilion DV6000 Athlon 64 X2 1.7Ghz) but also when I try to get back in windows to research some info about my problem, I was shock to discover that I ruined my Windows Vista, I try some quick fixes to get back in graphics mode but nothing works so I end up re installing from partition (good thing this is a brand new laptop so I didn't t loose anything) I use the same Ubuntu Live DVD in both laptops and my HP DV6000 works pretty well on Linux, also both laptops uses x64 so I'm don't think the problem is the version of the OS or the DVD it self, when I try to load the Live dvd I get the PIDOF error first after a while goes on and then I get the xserver config error I set the configuration in the xserver and the progran goes on loading the live DVD but never finish the installation, I'm yet to try another time with a newly downloaded version of Ubuntu Gusty 7.10 x64,  I don't know what to do now I'll appreciate all the help possible I'll even try any other distro of Linux before settle to run on Vista for the time being. Thanks for the help

PIDOF [3266] can't read sid from proc /1/stat
PIDOF [3266] can't read sid from proc /10/stat
PIDOF [3266] can't read sid from proc /11/stat
PIDOF [3266] can't read sid from proc /163/stat

---

### Post by Ikslewap on 2007-11-22
Hmm ok.  I would say try to download the x64 live CD, not the full distro DVD....You can download all the packages later with apt-get.   The error message you've shown could mean a # of things:  1) The download is actually corrupt and its not finding the data it wants on the proper sectors of the media (your DVD or CD) or 2) It is finding the data but it is corrupt.  without actually seeing your box it might be hard to do, but I am confident that Ubuntu will run on your system.  I'd say get a system running, so you can at least get on the website (which it looks like you can do already).  Go to ubuntu.com, download the 600 and some meg live install cd for x64.  Then follow the instructions in the download section on that site to compare the MD5 Sums.  This will verify that it downloaded without corruption.  If you are trying to get the full DVD running then there is actually a fair chance for corruption during download or media writing due to its size.  The chance for corruption of data is proportional to the size of the file.  Try the simple CD-R file for x64.  Its smaller and frankly you don't need the full dvd.  If your MD5 check is good, then try it.  Narrow it down, thats the way to go.  

You said that you might like another distro if you could at least get it working.  I could recommend a few but in my experience Ubuntu really has the best GUI.  That and its based on Debian which is a slim distro of linux but popular because it isn't "package happy."    

Happy Holidays,
Matt

---

### Post by Newbie1978 on 2007-11-22
Hello! first let me thank you for all the help, I all ready have downloaded the Ubuntu Gusty 7.10 live CD without all the adds ons of the Ultimate version, I'm yet to burn the disc but after that I will check it for errors as you say, and then I'll give it another go, my main concerned is that I have to re install again my Vista if I cant get it going, I've using Linux only for a while but I really like it, I actually fell that I learning more from Linux in a few months that I did with Windows all this years, last time I didn't pay that much attention to the errors but if I get some this time I'll write all of those down and posted here, well thanks again for the help

---

### Post by Newbie1978 on 2007-12-03
Hello, I try again to install Linux Ubuntu in my HP dv 6660SE, unsuccessfully this time I use Ubuntu 7.10 Gusty, first I get a message "UBUNTU IS RUNNING IN LOW GRAPHICS MODE" I hit continue soon after I get "error microcode bcm43xx_microcode5.fw not available" some other time after the "UBUNTU IS RUNNING IN LOW GRAPHICS MODE" I try to configure the drivers for the graphics card and the screens with the same result and the same error message "error microcode bcm43xx_microcode5.fw not available" I think the problem is the graphic card, Please help me at this point I only have Linux at work. Thank you

---

### Post by Newbie1978 on 2007-12-12
This is the answer to all my prays, I use this guide and it works just fine, just download the alternate CD amd 64 ubuntu 7.10 gusty and thats it, my HP Pavilion DV 6660SE is working great, go ahead and follow this guide.

[http://ubuntuforums.org/showthread.php?t=512059](http://ubuntuforums.org/showthread.php?t=512059)

---

