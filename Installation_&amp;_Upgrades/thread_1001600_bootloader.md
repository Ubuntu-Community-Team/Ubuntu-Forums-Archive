---
title: "bootloader"
date: 2008-12-04
forum: Installation &amp; Upgrades
---

### Post by farak on 2008-12-04
Hi,

I've been trying out different flavours of linux for the last while and have finally settled on Ubuntu as the one. I've had the other versions of linux installed on different partitions and in deleting these partitions to free up storage space I managed to screw up my bootloader. To fix this, I installed ubuntu on one of the free partitions and can now boot my machine. However, the bootloader recognizes this new installation as the main one and my original installation as one of the other operating systems with Wondows, and it also doesn't recognize any kernel upgrades that I've installed.

How can I setup the bootloader to use my original installation as default so I can safely delete the other partition?

---

### Post by dstew on 2008-12-04
I do not have a complete picture of your setup. Do you have two Ubuntu installations, your original and the other you used to rescue the system? If so, you should be able to re-install the grub boot loader so that it boots your original installation rather than the rescue installation. Is that what you want to do?

---

### Post by dabl on 2008-12-04
The *buntu bootloader is the _Gr_and _U_nified _B_ootloader, aka Grub. It is a tiny operating system that has the single purpose of booting your real OS(s).  Here's a good tutorial, with links to more sources, and includes examples of doing things like you need to do:

[http://kubuntuforums.net/forums/index.php?topic=3081671.0](http://kubuntuforums.net/forums/index.php?topic=3081671.0)

:)

---

### Post by farak on 2008-12-12
I have two versions of ubuntu - the original 8.04 version and 8.10 that I used for rescue. For the moment, I can't get the acer_acpi working under 8.10 so I want to stay with my original installation. I have read some posts that say to change the menu.lst file, but I want to be able to delete the partition that 8.10 is installed on. How can I get my computer to look at the menu.lst in my original /boot/grub directory?

---

### Post by caljohnsmith on 2008-12-12
> **farak said:**
> I have two versions of ubuntu - the original 8.04 version and 8.10 that I used for rescue. For the moment, I can't get the acer_acpi working under 8.10 so I want to stay with my original installation. I have read some posts that say to change the menu.lst file, but I want to be able to delete the partition that 8.10 is installed on. How can I get my computer to look at the menu.lst in my original /boot/grub directory?
To help us get a clearer picture of your setup, first open a terminal (Applications > Accessories > Terminal) and please post:
```
sudo fdisk -lu
sudo xxd -l 2 -p /dev/sda
sudo xxd -s 1049 -l 2 -p /dev/sda
```
Note that "-l" is a lowercase L, not a one. Also, please identify which is the 8.04 partition.

---

### Post by farak on 2008-12-24
Here's the output:

fdisk -lu

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x19b9be03

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   185598944    92799441    7  HPFS/NTFS
/dev/sda2       185598945   488392064   151396560    f  W95 Ext'd (LBA)
/dev/sda5       185599008   248798654    31599823+  83  Linux
/dev/sda6       248798718   468873089   110037186   83  Linux
/dev/sda7       468873153   488392064     9759456   82  Linux swap / Solaris
root@TolBrandir:/home/mac# xxd -l 2 -p /dev/sda
eb48
root@TolBrandir:/home/mac# xxd -s 1049 -l 2 -p /dev/sda
04ff
root@TolBrandir:/home/mac# 

8.04 is on sda6 and 8.10 is on sda5. When I boot my system GRUB uses the /boot/grub/menu.lst from sda5 for the list of installed OS's.

---

### Post by caljohnsmith on 2008-12-24
OK, to give your 8.04 sda6 partition control of Grub in the MBR, try this:
```
sudo grub
grub> root (hd0,5)
grub> setup (hd0)
grub> quit
```
If none of the above commands return an error, reboot, and let me know if you get your 8.04 menu.lst OK on start up.

---

### Post by farak on 2008-12-24
OK, so I got no errors when I typed the commands and after the reboot I got my 8.04 menu.lst. But, when I tried to select the 8.04 OS I got an ERROR 22 no such partition. Now I can't boot Ubuntu at all.

---

### Post by caljohnsmith on 2008-12-24
OK, how about trying this next: when you get the Grub menu on start up, select the first Ubuntu entry, press "e" to edit it, select the line that says "root (hdX,Y)" where X and Y are numbers, press "e" to edit it, change it to "root (hd0,5)", press return to save the change, then press "b" to boot. Based on the info you gave, I think that should be all it takes to boot Ubuntu. Note that the above change is not permanent, so you'll need to modify your menu.lst to make it permanent.

So if it works, when you get into Ubuntu, just do:
```
gksudo gedit /boot/grub/menu.lst
```
And change the line that says "#groot=(hdX,Y)" to use the (hd0,5) that worked to boot Ubuntu. Save, quit gedit, then run:
```
sudo update-grub
```
And you should be all set. Let me know how it goes or if you run into problems.

---

### Post by farak on 2008-12-24
Legend!! Everything's working perfectly now. Thanks for the help caljohnsmith

:guitar:

---

### Post by caljohnsmith on 2008-12-24
Glad that did the trick, farak; cheers and happy holidays. :)

---

