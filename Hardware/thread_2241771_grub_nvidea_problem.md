---
title: "grub nvidea problem"
date: 2014-08-28
forum: Hardware
---

### Post by Loki*PI on 2014-08-28
I've been battling this off and on for several weeks. I've read lots of posts and tried any number of suggestions.

I've a new system - GigaByte B85M-HD3 - 4 channel with 8 gb memory, I-i5 4460 CPU.
 video card - ASUS NVidea GeForce 630 2 Gb memory 
1 Tb hd for Windows 7 and games
2 other hd that I have Ubuntu 14.04 installed on.

I tried to do dual boot but eventually gave up on it. My solution was to simply disconnect the Ubuntu hard drives and power up the Win 7 drive when I need it. This works fine as most of the time run U-14. 

My problem is I cannot get U-14 to support the NVidea card. In one posting I read that the i915 driver has a problem and in BIOS you have to enable Legacy Option ROM. OK did that - nothing. I've also read about adding nomodeset to GRUB2 to get into the desktop so you can add 'additional drivers', doesn't work.  Also acpi=off, acpi= , any number of things none of which have solved my problem.

I don't know if this is a secondary problem or part of the video issue but I cannot get into the GRUB page consistently. Perhaps once in every 6 or so reboots I can get into grub holding down shift key.  Most of the time the system by-passes the GRUB page and I get a row of dots across the sceen four dots high, and lower part of the screen is purple.

When I can get to GRUB I have tried the nomodeset and everything else I've seen suggested and nothing happens. On F10 the screen will stay black for several seconds then flash purple with something written on it that I cannot read then go black and the system will either just set or reboot.  

I've done several reinstall and the situation doesn't change.  If I pull out the NVidea card and just run off motherboard video no problem.

Extremly frustrated dosen't really cover it. Any suggest would be much appreciated.

---

### Post by christopher9 on 2014-08-28
What video driver IS being used ? Do you also have an integrated video card that does work ? When you run Software Updater, do you have proprietary Nvidia drivers as an option ?

---

### Post by Loki*PI on 2014-08-28
Thanks for replying: 
The driver being used is i915
If I pull the Nvidea card the video on the motherboard works fine.
To get to desktop to run software update I have to pull the Nvidea card. Without the card installed update does not give an option to install Nvidia drivers.

---

### Post by christopher9 on 2014-08-28
Use the Settings option of the Software Updater and go to Additional Drivers...

---

### Post by Loki*PI on 2014-08-28
Settings in Updater? There is a tab for Additional Drivers but it is blank.  What I've seen before is if you have, for example, an Nvidea card installed, then in 'additional drivers' you would see some options for that card. If there is no card then no options.

---

### Post by Loki*PI on 2014-08-28
What I think I need is a way to get GRUB to work so that I can get to the desktop with the Nvidea card installed. Then I can go to Additional Drivers and install the drivers for the card. I think after than I'll be good. I can't get to desktop with the card installed. NOMODESET is suppose to be the solution from what I've read but doesn't work in this case.

---

### Post by Loki*PI on 2014-09-01
For those struggling with a similar issue I'll update this, I've done more research but haven't solved the problem.  

By editing the Linux line in GRUB I was able to get to TTY1 with the Nvidea card install. The edit I used was remove quiet splash and remove VT-handoff=7, I then put in nomodeset splash --verbose text. I thought once I got to TT1 I would be able to use command line to install nvidea drivers using the commands from "ubuntuforums.org/showthread.php?t=1743535&highlight=grub+2+nvidea" which is a very good discussion of this problem, but nothing worked. 

There is a ppa at 'http://www.ubuntuupdates.org/ppa/xorg-edgers' that I understand is suppose to have the nvidea drivers but the ppa site has a number of warnings not to use it. When I try to add the ppa it fails. 


I was able to look up on Nvidea the correct driver for my card, 340.32, release 2014.8.12 but I haven't found it anywhere yet in a ppa. Early in this process I tried to install drivers directly from Nvidea and ended up having to rebuild my system. Not sure what happened but I'm not eager to try that again. 

This is all WAY to complicated and time consuming just to add a video card. As brillant as Ubuntu is I think some of the basics have been skipped over to do the more fun sexy stuff. Installing a video card should not take weeks of research, multiple rebuilds, etc.

---

