---
title: "Ubuntu 9.04 installs, but boots into XP without options.. how do I boot into Ubuntu?"
date: 2009-05-26
forum: Installation &amp; Upgrades
---

### Post by nurvzy on 2009-05-26
I'm trying to install Ubuntu 9.04.   I have a relatively newish computer Dell Intel Pentium 4 3.2GH, 1GB Ram, NVidia 6800, with two harddrives.

HD1(110GB): Windows XP Partition (55GB) || NTFS (55GB)
HD2(300GB): NTFS (297GB) || Unpartitioned(3GB) 

The second hard drive I installed myself and when run the Ubuntu install it wants to install on the HD2, not the partition I made for it on HD1.  So I go into the advanced partition knowing just enough to be extremely dangerous apparently.

I find the free partition on HD1 and re-format 'ext3' and mount '/' (hoping that's the right thing to do).  Then I make the Unpartitioned 3GB on HD2 the 'swap disk'.   I think I'm happy with what I've done and click install.

It runs, says its complete, reboots, asks me to remove the CD... and now when I reboot it just goes right into XP no options, no nothing, just bam windows.  I look at windows explorer and sure enough windows can't see the partition I made for Ubuntu (which I think is a good sign).

Is there something I can do to the boot.ini (or something) to tell it to give me the option to boot from the new ext3 partition drive?

Did I screw up the install?  The end result I would like a dual bootable system of XP/Ubuntu.   Unfortuantely, I'm pretty green with Linux. :(

Please, any help/advice would be **much** appreciated.

Thank you,
Nick

---

### Post by nurvzy on 2009-05-26
So I ran the little tutorial I found at: 
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

sudo grub
find /boot/grub/stage1
---> (hd1,4)
root (hd1,4)
setup (hd0)
quit
sudo reboot

I didn't get any errors, grub said it was all success. But still no different result, after reboot it goes right back into XP -- without option. =(

Ugh *sad panda face*

---

### Post by nurvzy on 2009-05-26
Derp.  After reading more about grub, I realized I need to run setup (hd1) instead of setup (hd0).  All is good in the world.  Ubuntu dual boots with XP.  Hurray!

---

### Post by mindbust on 2009-05-26
Had the same issue. I figured out i just need to take time and read those ql ubuntu tuts. Big thx to creators.

---

