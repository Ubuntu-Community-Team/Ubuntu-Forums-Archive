---
title: "ubuntu 8.10 install hangs!  Please help!"
date: 2009-03-31
forum: Installation &amp; Upgrades
---

### Post by windows_sucks on 2009-03-31
Hello,

I've downloaded ubuntu 8.10 ISO and burned it into CD.  

My PC boots fine with the ubuntu CD.

I have checked the CD in ubuntu main menu and it seems to be OK.

When I start the installation from the menu, I see blue bar moving left to right. I see CD ROM and HDD spinning.

Once the moving blue bar completes, CDROM and HDD seem to stop spinning for few seconds then PC tries to show GUI.  

This is where it hangs or crash.  Sometimes I see GUI (just the background) with mouse pointer visible, but the pointer does not move.  

Sometimes I don't even see the GUI, I get blank screen and signal to monitor gets cut.

Can anyone please suggest what I can try??

Thanks.

---

### Post by KCG102282 on 2009-03-31
What are your system specs?

---

### Post by windows_sucks on 2009-03-31
KCG102282,

I have:
CPU: AMD XP 2000+ 
MB: Gigabyte GA-7VRXP
CDROM: Lite-on 24X R/W.
Video: Radeon 9600 AGP
RAM: 512MB (cannot remember what brand or channel)
HDD: 40GB IDE 
PCI Device: 1 Wireless Network card. 
NO USB devices attached.

Thank you.

---

### Post by KCG102282 on 2009-03-31
It is probably the Video card that is giving you the problems I have the same issue with my ATI card. What I would do is download and burn the alternate cd and Install Ubuntu that way. Once that is done go in recovery mode and load the root terminal and enter nano etc/X11/xorg.conf and change your video card driver to Vesa. Then install the proprietar driver and you should be good to go.

---

### Post by windows_sucks on 2009-03-31
Thanks a bunch!  I'll give that a try!!

---

### Post by windows_sucks on 2009-04-01
I have downloaded ALT version CD.  
Installing process hangs while "configuring linux-image-2.6.27-7-generic" which is 83% of the installation.  Anyone know how to get around this??

Thanks.

---

### Post by Zekes on 2009-04-01
I also have this problem, and think it is a problem with amd 64 bit machines. I found that holding down spacebar allows the boot sequence to continue, it may be inconvenient but it is a temporary fix until you can figure out what is wrong.

---

### Post by KCG102282 on 2009-04-01
> **Zekes said:**
> I also have this problem, and think it is a problem with amd 64 bit machines. I found that holding down spacebar allows the boot sequence to continue, it may be inconvenient but it is a temporary fix until you can figure out what is wrong.
I have a 64bit machine and my ubuntu works fine.

---

### Post by KCG102282 on 2009-04-01
> **windows_sucks said:**
> I have downloaded ALT version CD.  
Installing process hangs while "configuring linux-image-2.6.27-7-generic" which is 83% of the installation.  Anyone know how to get around this??

Thanks.
Did you burn the dis at the slowest speed?

---

### Post by windows_sucks on 2009-04-01
> **KCG102282 said:**
> Did you burn the dis at the slowest speed?

No, I did not.  Although I burned at 8X.

---

### Post by KCG102282 on 2009-04-01
I would burn it at the slowest speed and make sure the checksum matches up before trying again.

---

### Post by windows_sucks on 2009-04-01
Holding spacebar actually got through the point I was stuck at (I don't know how that helped), but I am stuck again when configuring anguage-pack-en-base 1% or so...

Please help!

---

