---
title: "CD-Rom &quot;lost&quot; during install"
date: 2005-01-25
forum: Installation &amp; Upgrades
---

### Post by sbaker33 on 2005-01-25
Hey,
I am a real noob when it comes to Linux ad I am running into trouble installing on a Toshiba laptop.  It doesn't have an internal CD so I am booting from an external.  I can get it to boot the loader for Ubuntu as well as other distributions but once it boots it can't seem to find the CD-Rom anymore.  The CD-Rom is USB and not from Toshiba it is a little slow and old as well.  It seems to work just fine under WinXP, which is what is installed currently.  I don't have a floppy drive and when booting from a PC-Card CD-Rom I get the same result.

I have seen how tos showing how to install Fedora Core, SuSE and Debian from a network boot from the SD card.  But would prefer to install Ubuntu and do so from CD, if possible.


Any ideas?

---

### Post by marc_erick on 2005-01-26
I too am having the same issue trying to install Ubuntu on my Dell Latitude d600. The goal: Install Ubuntu on my hot swapable hard disk, using my usb external dvd writer to boot the install cd. I can boot the install CD, but the install fails at the point where it asks me to install cd drivers from a boot floppy. I've been able to install Libranet with success (but they have a particular boot option ([http://libranet.com/support/2.8/0310](http://libranet.com/support/2.8/0310)). It would be nice to have this option in Ubuntu. There is also some discussion at MEPIS about a workaround ([http://www.mepis.org/node/view/4898](http://www.mepis.org/node/view/4898), [http://www.yyhh.org/blog/2005/01/install-mepis-linux-on-ibm-thinkpad.html](http://www.yyhh.org/blog/2005/01/install-mepis-linux-on-ibm-thinkpad.html)). The MEPIS solution was to copy the files onto the partition you want to install and reboot with the MEPIS cd. I haven't tried this. The ProMEPIS partition (2.6 kernel), apparently, has to be ext3 formatted first before copying the files over. I'll try it in the next day or so, unless there's someone who knows how to do it.

---

### Post by sbaker33 on 2005-01-28
Have you tried the libranet switch with Ubuntu?  I will try both of these options this weekend (if I can get my hands on the USB CD ROM again :cry: ).  Good luck and let me know if either one works for you.

---

