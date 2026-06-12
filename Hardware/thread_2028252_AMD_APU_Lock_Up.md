---
title: "AMD APU Lock Up"
date: 2012-07-17
forum: Hardware
---

### Post by charels88 on 2012-07-17
I have put a HTPC together with an AMD APU 3870K and have been unable to prevent it from locking up every 15 min or so.  I'm running Ubuntu 12.04 64-bit and have tried various ways of installing the AMD supplied drivers.  I have been following this ([http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide)) tutorial on installing the driver.  Each time I failed at getting the driver to take I would re-install Ubuntu and update to try again.  First, I went with the driver provided by the additional drivers program but no change.  Next, I downloaded Catalyst 12.6 from Amd's site and used the tutorial to manually install the drivers and yet again it would still lock up.  


HTPC Specs:
Asrock A75m mobo
AMD APU 3870K @ Stock
2x2GB OCZ 1600MHz RAM (6-8-6-24) 1.65V
120GB SATA HDD
Rosewill RNX-N250PC2 Wifi Card
Old Dell Dimension Case w/PSU

---

### Post by charels88 on 2012-07-18
I tried installing Catalyst through additional drivers on a fresh install with no updates and still no change.  I tried to follow the tutorial to uninstall catalyst and there was no uninstall file in the ati folder, amd folder and the fglrx folder.  By installing the driver through additional drivers it should install all dependencies right?  I would love to have this problem resolved so I wont have to revert to an old copy of XP.

---

### Post by steeldriver on 2012-07-18
AFAIK if you install through the 'Additional Drivers' OR from the AMD/ATI installer with --buildpkg option there won't be an uninstaller script - it's only really required if you run the installer without --buildpkg (otherwise you can use apt-get to uninstall it)

What makes you so certain it's a driver issue? I have a mythbuntu box with the A8-3870K on an ASUS board (granted it's 11.10 not 12.04) and it's fine - I think I tried every driver release from  12.3 to 12.6 at one point (trying to get HDMI audio working - which turned out to be an ALSA issue) - right now it's got the 2:8.881-0ubuntu4.1 packaged version

---

### Post by charels88 on 2012-07-19
Thanks for the reply but I dont know if its a driver issue.  Did your issue with the ALSA driver cause lock ups or just no hdmi sound?  I will comb through and see if I can locate another source of my problem.

---

### Post by steeldriver on 2012-07-19
My ALSA issues just manifested as lack of sound

Lockups are really hard to diagnose in my (limited) experience - you can narrow it down a little e.g.

- can you still switch to the virtual terminals (Ctrl-Alt-F1 etc.)? if so it's most likely something 'higher' than the xserver (i.e. at the display/session layer)

- (if you have ssh enabled) can you still ssh in? if so it's most likely graphics driver or 'above' but not kernel

- is caps lock still responsive (i.e. does the caps lock light toggle if you press it)? if not then it's likely kernel or hardware

Depending on those answers you could trawl through ~/xsession-errors, /var/log/Xorg.0.log, /var/log/dmesg, /var/log/kern.log

Good luck

---

### Post by charels88 on 2012-07-24
Thanks for the tips and I could enter a virtual terminal after a lock up.  Too bad it wouldn't restart my computer without me doing a hard restart.  I gave up on using fglrx and went with the Gallium driver.  I will try getting fglrx working with another version of ubuntu earlier than 12.04 when I finish watching my seasons of Futurama lol....  Thank you steeldriver you have been a big help.

---

### Post by charels88 on 2012-07-24
I still have the frequent lock up problem but it is not the graphics.  I was at my gf's for the weekend and took my htpc to finish working on it and I was forced to use LAN since her router doesn't work with Ubuntu at all.  I had no problem with lockups while I was there and now that I'm home and using wireless again I still lock up.  This thread can be closed and I will have to do more homework next time I begin looking for answers for problems I dont have.....

---

