---
title: "Failed Upgrade to 9.04"
date: 2009-06-03
forum: Installation &amp; Upgrades
---

### Post by imple on 2009-06-03
Hi,

I upgraded from 8.10 to 9.04, but when restarted ubuntu fails to boot. I get the same screen as this  [http://dominikengbers.gmxhome.de/bug.JPG](http://dominikengbers.gmxhome.de/bug.JPG) (with different version numbers). If I type exit at the prompt (even after waiting a long time) it still doesn't boot :( 

What can I do? Is there any way to repair the installation? Surely my hardware must be compatible if it was compatible for 8.10?

Thanks

---

### Post by imple on 2009-06-03
any ideas?

---

### Post by dstew on 2009-06-03
I assume you got a grub menu, and picked one of the menu items. It is possible that the grub kernel menu item has the wrong kernel root disk designation. Press 'e' for edit at the grub menu, and post to the forum the commands for the menu item that is failing. There are usually at least four commands, root, kernel, initrd, and boot. Also, boot a Live CD and post the output of```
sudo fdisk -l
```Then we can compare the kernel root designation with what is actually in your system.

---

### Post by mckemie on 2009-08-04
I'm not imple, but I've just encountered the same or similar problem.  I have a multi boot set up with 8.10 upgraded to 9.04 on my sda7:
---
mint6-32 2009 # fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa43ca43c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7296    58605119+  83  Linux
/dev/sda2            7297        7311      120487+   c  W95 FAT32 (LBA)
/dev/sda3            7312       14593    58492665    5  Extended
/dev/sda5            7312       10138    22707846   83  Linux
/dev/sda6           14291       14593     2433816   82  Linux swap / Solaris
/dev/sda7           12982       14228    10016496   83  Linux
/dev/sda8           14229       14290      497983+  82  Linux swap / Solaris
/dev/sda9           10139       12857    21840336   83  Linux
/dev/sda10          12858       12981      995998+  82  Linux swap / Solaris
---

Right now, I'm running Mint off of sda1 and have sda7 mounted.  I was thinking that I had /boot on a partition and shared by all installs, but that seems to be not the case.  There are some differences between the /boot under sda1 and the one (failing) on sda7.

Before I upgraded sda7 to 9.04, all partitions would boot.  Afterward, no go on sda7; no complaints, just a blank screen after I select sda7 with grub.

I wonder how I should go about straightening this mess out?  I see the installs are not sharing a swap partition as they should.

---

