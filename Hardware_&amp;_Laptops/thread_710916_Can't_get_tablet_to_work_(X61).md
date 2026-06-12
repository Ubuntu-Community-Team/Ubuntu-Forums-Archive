---
title: "Can't get tablet to work (X61)"
date: 2008-02-29
forum: Hardware &amp; Laptops
---

### Post by adamsad1 on 2008-02-29
Hey all,

I'm completely new to Linux and coming over from Vista. I have a Lenovo X61t and am trying to get my tablet to work, but I'm not having any luck. I've uncommented the three lines under "uncomment this if you have a wacom tablet" and that didn't work. I've followed  [_this guide_]("http://ubuntuforums.org/showthread.php?t=590747&highlight=tablet") and updated both xorg.conf and wacom driver, and still no luck (however I couldn't get wacom-tools to install... sudo aptitude install wacom-tools came back saying it couldn't find the package).

When I do lsusb I get:

Bus 005 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 001 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  

which is different than what other users [_here_]("http://forum.tabletpcreview.com/showthread.php?t=11988") were getting (they had Wacom show up... Along with RealTek, but I'll worry about that when I get there...)

I'm sorry if this has already been dealt with elsewhere. I couldn't find any solutions other than what I already tried.

Thanks.

---

### Post by adamsad1 on 2008-02-29
Well, not sure what happened but all of a sudden my stylus is working... Kinda. I can move the cursor around smoothly, but when I press on the screen it freaks out and rapidly left clicks two spots on the screen around my stylus...

---

### Post by schmolch on 2008-03-01
Im using the X60T.
When you make these changes to xorg.conf you need to restart X (log-out or ctrl+alt+backspace to kill it).
"sudo apt-get install wacom-tools" really should work, maybe you made a typo.

Do you have the multitouch? I dont know if there is support for it yet.

Btw. the wacom is a serial device and not usb. Usb-Tablet-PCs are not support by the current linuxwacom driver.

If you have any other tablet-related questions just shoot!

---

