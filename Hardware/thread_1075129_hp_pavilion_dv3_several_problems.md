---
title: "hp pavilion dv3 several problems"
date: 2009-02-19
forum: Hardware
---

### Post by cecilmoney on 2009-02-19
This machine is not taking to well to its new install of 64 bit ubuntu.

So far three problems have presented themselves: 
1. the wifi doesn't work 
2. When headphones are plugged into the headphone jack, the speakers are muted, but nothing comes through the headphones. 
3. I have laggy/choppy video playback (I have compiz completely turned off)

I solved the 1st problem [http://ubuntuforums.org/showthread.php?t=1072051](http://ubuntuforums.org/showthread.php?t=1072051) , but I still need help with the other two.

If you have any advice on solving these problems, please let me know.

---

### Post by cecilmoney on 2009-02-20
I was running 32 bit ubuntu before, and I'm pretty sure that I didn't have any problems with flash/streaming video, so I might just downgrade. 

If no one can help, that is.

---

### Post by cecilmoney on 2009-02-20
I think I'm running the ati radeon hd 3200 graphics card, and I currently have the ATi/AMD propriety FGLRX driver activated.

---

### Post by cecilmoney on 2009-02-20
I did some work on my volume control settings and figured out why my audio out wasn't working, it had been muted. No idea why, but it was an easy fix.

Anyway, the only problem I have now is the choppy flash playback. It seems to work fine on some sites and run poorly on others. I'm guessing there is nothing i can do, so that basically makes this thread useless.

---

### Post by systm on 2009-05-05
check and make sure that you are using the most up to date drivers.

Side note, does yours allow you to install a different sata drive in it or does it not recognize any like mine does?

systm

---

### Post by texadactyl on 2009-05-05
I attempted a 64-bit 9.04 installation on my wife's brand-new dv3 notebook.  I am an experienced Ubuntu user as well as advanced installer of hardware and software.  The bottom line is that I was forced to give up on my wife's dv3 notebook (for the time being) due to time constraints and the inability for Gnome to solve some issues out of the box in an automatic fashion.  Sorry if I appear impatient but the dv3 was not for me;  the "client" (my wife) was waiting to get down to work.

Personally, I am commited to Ubuntu on my personal workstation with a conventional mouse and an Ethernet connection.  If the dv3 had been for me, I would have (somehow) solved all of the issues and posted them here.

Xorg worked with a generic vesa driver right away.  Excellent.  A few times in the past, Ubuntu has forced me to use a second PC while the target machine was in command line.  This is a big help to an installer.

The first thing I did was activate the proprietary Broadband wifi driver and the ATI fglrx driver that was offered to me from the admin/hardware drivers selection.  Then, I installed ubuntu-restricted-extras in order to get components such as the 64-bit Sun JRE plugin for Firefox.

Gnome wifi support successfully found my router but did not help me very well with making the WPA2 connection.  I did the manual (ugh) work-around from the Ubuntu forums for wifi and it worked well.  Thank you, forum!  However, 

[INDENT](a) The Gnome applet really should let you enter the password, compute the hex-string based on the password and SSID, update the wpa config file, and restart wifi (automation).  Other OSes automate this for the user.

(b) Reconnect should be checked ON for the user by default.  Why would I not want a connection re-attempted?  There might be an obscure case but most folks would like this done automatically, I believe.

(c) The Broadcom driver was unstable, losing my connection over and over again, even after I checked the automatic reconnect box.  My Broadcom hardware supports b/g/n as does my router.  My wife needs "n" support where it is available for her notebook.  I do not know if this is a Broadcom driver issue or a hackable settings issue.  It should be automated and reliable.[/INDENT]

I had no sound at all.  This is probably solvable as I had these issues in the past with Ubuntu out of the box.

The worst thing to my wife was the touchpad support.  This is probably solvable.  The symptom is that the touchpad is hypersensitive (runs all over the screen and clicks things).  Other OSes provide a wizard to guide you through adjusting touchpad or mouse sensitivity.  I didn't really know where to start except through Googling or searching the Ubuntu forums.

Anyways, I would welcome being told what I overlooked.

9.04 on a workstation is such a pinnacle of accomplishment for the development team.  I am truly impressed.

-Richard

---

### Post by systm on 2009-05-07
I agree Richard, but you have to understand, it's not the devs fault that our model isn't supported well, its the Chip Devs and the laptop manufacturers that are causing such problems.  Just to let any dv3(InsydeH2O BIOS) Users, you will not be able to install a new HDD, Wifi, or use OS X (at least with Hd3200).  
I too have the audio issue, broadcom driver has gotten more stable, still not open source tho.

---

### Post by texadactyl on 2009-05-08
Agreed about drivers.  

Ironically, on Windows 7, the drivers from the same manufacturers (E.g. Broadcom) provide stable drivers. I suppose its just a matter of return on investment like everything else.  There's no profit in open systems for Broadcom nor HP.

On my iMac circa October 2007, the proprietary Ubuntu hardware drivers (Broadcom and ATI) run fine.  Lucky, I guess.

However, Wi-Fi WPA2 password entry ought to be seamless without the forum work-around.  The current state of that applet is not very polished.

---

### Post by zeroseven0183 on 2010-07-08
I'm planning to buy an HP Pavilion dv3 this week and after reading this thread, I'm wondering if Ubuntu 10.04 would work smoothly. If not, I'll choose another brand/model.

Any thoughts?

---

### Post by lidex on 2010-07-09
[http://ubuntuforums.org/showthread.php?t=1258788]("http://ubuntuforums.org/showthread.php?t=1258788")
[http://linux.aldeby.org/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops.html/3#nvidia_ati]("http://linux.aldeby.org/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops.html/3#nvidia_ati")

---

