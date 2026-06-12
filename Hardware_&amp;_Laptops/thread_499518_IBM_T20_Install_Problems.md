---
title: "IBM T20 Install Problems"
date: 2007-07-12
forum: Hardware &amp; Laptops
---

### Post by kdonovan on 2007-07-12
Hi! I'm new to Ubuntu and am trying to get it installed on my old T20 laptop. It's a 700mhz model with 256mb RAM. Everything else was standard. I've scanned some of the previous threads, but can't really find what I'm looking for, so here it goes :)

Basically the damn thing won't load the CD. I've checked the BIOS settings and the DVD drive is above the hard drive in the boot order, tried hitting that F12 Button/boot menu to run it that way, turned OFF the hard drive in the BIOS boot order to force it to boot THAT way, but no luck. I've also tried to Alternate CD. Both CDs do work because I've tried them out on my primary comp and it boots from the CD fine. Am I completely missing something here? Any suggestions would be appreciated :)

---

### Post by kdonovan on 2007-07-12
*bump* anyone?

---

### Post by mumbles on 2007-08-04
I have exactly the same problems, i can get it to boot with a 5.10 install cd but not with dapper. 

When i upgrade loads up to a point , then stops and a curser shows up. There is hdd activity but i cannot get anything. Any ideas?

---

### Post by abrianb on 2007-08-19
I installed 6.06  with the bios set to default with no problems. I have since upgraded twice and am now running 7.04 feisty with very few problems.
The T-20 that I own is a type 2647-86u. I do not run it dual-boot and never tried. When I loaded the DVD I elected to go right into install.

---

### Post by dogbreath97006 on 2007-09-20
I too am having issues with my T20 and UBuntu 7.04.  I have 256M RAM, so--at least in theory--I should be able to make this work.

By changing the default display mode away from PCI and then using the "safe graphic mode" boot option, I can get the display manager to load.

However, the CD-ROM grinds away continually, and it's pretty much impossible to get the install application to completely load. I waited 24 hours, and the Trash applet died but no "continue" button showed up on the screen.  Response--including the mouse--is impossibly slow, and I started to worry about the duty cycle on the CD-RW drive, so I killed it without actually starting the installer

I'd be grateful for any hints on how to proceed from here.

---

### Post by Fran89 on 2007-10-01
> **dogbreath97006 said:**
> I too am having issues with my T20 and UBuntu 7.04.  I have 256M RAM, so--at least in theory--I should be able to make this work.

By changing the default display mode away from PCI and then using the "safe graphic mode" boot option, I can get the display manager to load.

However, the CD-ROM grinds away continually, and it's pretty much impossible to get the install application to completely load. I waited 24 hours, and the Trash applet died but no "continue" button showed up on the screen.  Response--including the mouse--is impossibly slow, and I started to worry about the duty cycle on the CD-RW drive, so I killed it without actually starting the installer

I'd be grateful for any hints on how to proceed from here.

THE same thing happens to me if somebody could help me i have a T23 yes also tring to install Ubuntu 7.04 and also have the 256 RAM i cant get the Live CD to work, any help is apreciated, i will try the alternate CD later but so far no luck with the Live CD

---

### Post by Fran89 on 2007-10-02
Well tried the Alternate Install CD but could not get pas partitioning because i did not have enough disk space:( I really hope i could install but all i can give is 4GB i really hoped this was enough because i have a 20Gb of which i only have 6.91 Free and wanted to leave a few GB for windows to run, so i can't. Alternate CD fixes the Live Cd's problem nonetheless so Dogbreath97006, and anyone else that encounters this problem that's your answer Alternate CD :)

---

### Post by dogbreath97006 on 2007-10-03
Update: I have successfully installed Ubuntu on an IBM T20 and an IBM T22.

The issue has to do with the display driver.  Use the "alternate CD" (non-graphic installation).  Then, before attempting to light up X Windows, modify your xorg.conf per the following link:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-savage/+bug/33617](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-savage/+bug/33617).

(Changing the device from "savage" to "vesa" also works but is rather drastic).

Detailed instructions from the above link:
--------

Daniel James wrote on 2006-04-22: (permalink)

This appears to be a hardware bug. See [http://www.thinkwiki.org/wiki/Problem_with_video_related_system_lockup](http://www.thinkwiki.org/wiki/Problem_with_video_related_system_lockup) and [http://mailman.linux-thinkpad.org/pipermail/linux-thinkpad/2006-March/032672.html](http://mailman.linux-thinkpad.org/pipermail/linux-thinkpad/2006-March/032672.html)

Adding

Option "BusType" "PCI"
Option "DmaMode" "None"

to the "Device" section in xorg.conf fixed the issue for me.

---

