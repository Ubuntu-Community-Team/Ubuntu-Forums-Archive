---
title: "GRUB error 21"
date: 2009-10-11
forum: Installation &amp; Upgrades
---

### Post by Rick Abraham on 2009-10-11
My main HD has Win XP installed on it and I had a second HD spare so I installed Ubuntu on it after finishing the Ubuntu installation it rebooted my PC as normal. But when GRUB tried to load the boot menu it gave me a error 21. How can I fix this ? I downloaded supergrubdisk but have no idea how to use it being a Linux newbie. Any help would be great

---

### Post by Bartender on 2009-10-11
I've built a SuperGrubDisc too and I also did not find it very easy to use.  I was never sure if I'd done something or not, just kept clicking around in circles.

Here's the GRUB Manual webpage

[http://www.gnu.org/software/grub/manual/grub.html](http://www.gnu.org/software/grub/manual/grub.html)

Look down towards the bottom for lists of errors created by GRUB Stage1, 1.5, and 2.  Error 21 is a Stage 2 error:

21 : Selected disk does not exist
    This error is returned if the device part of a device- or full file name refers to a disk or BIOS device that is not present or not recognized by the BIOS in the system. 

There are a million Error 21 hits in Ubuntu Forums and Google.  The first thing you might want to try is go into your BIOS and make sure that the second HDD is "enabled" in the boot menus.  Some BIOS'es don't automatically allow a new device to act as a boot device.  In a case like this, you would be able to install Ubuntu just fine, but when it comes to booting from that drive, no go.

---

