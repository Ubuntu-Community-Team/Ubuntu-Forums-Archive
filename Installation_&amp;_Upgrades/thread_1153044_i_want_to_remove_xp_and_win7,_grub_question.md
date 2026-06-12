---
title: "i want to remove xp and win7, grub question"
date: 2009-05-08
forum: Installation &amp; Upgrades
---

### Post by jonndoe45 on 2009-05-08
Ok, here is the setup, /dev/sdb is my boot disk, this is what fdisk reports:

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        7649    61440561    7  HPFS/NTFS
/dev/sdb2            7650       15298    61440000    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sdb3           15298       84501   555873258+   7  HPFS/NTFS
/dev/sdb4           84502       91201    53817750    5  Extended
/dev/sdb5           84502       89904    43399566   83  Linux
/dev/sdb6           89905       91201    10418121   82  Linux swap / Solaris

I want to remove sdb1-3 and increase sbd3 (4) with the space provided. 

I know how to use the partition editor, but what do I do about grub as it resides on /dev/sdb1 ?

I am a newbie, but I am ok using the command line etc. Any help is appreciated!

Thanks in advance.

---

### Post by dstew on 2009-05-08
Grub consists of two parts, stage 1 and stage 2. Stage 1, the boot loader, is usually installed into the Master Boot Record (MBR) of a disk. Stage 2 is found in the /boot/grub directory of your Linux system partition. Since the MBR is not a part of any partition, and since your Linux system partiton is sdb5, if you remove sdb1 grub will still be there. There is a chance that grub will need to be re-configured though, because the total number of partitions is changing. I am not sure about this last part. But, it is easy to re-install or re-configure grub if you have to.

---

### Post by kay-man on 2009-05-08
You will most definitely have to reconfigure grub, because you'll be removing partitions which will affect the partition numbering. After that grub won't be able to find your boot partition anymore, because it will have a different number.

This is very easy to correct, though.

In a terminal, run

sudo grub

This will open a grub session.

then run:

find /boot/grub/stage1

Grub will say something like (hd0,X), where X is a number.

Then you run

root (hd0,X)

and setup (hd0)

and you should be done.

You're instructing grub where to find the boot partition and writing this info to the MBR of your hard drive.

When you reboot for the first time, keep a live CD handy just in case :)

---

### Post by jonndoe45 on 2009-05-08
Have a live cd handy, thanks!

Silly question, but removing partitions doesn't affect theMBR does it ? And although my linux partition is on sdb4, its part of sbd3 which is an extended partition, I don't have to do anything with this (apart from resize it) ???

Thanks again for all the help, I can finally be free from Windows and Gates

---

### Post by kay-man on 2009-05-08
No, it won't affect the MBR, and the partition being contained within an extended partition is no problem at all. In fact, it's very similar to my own setup. I have by now deleted all but the last of my windows partitions and put the diskspace to better use, so I can tell you from experience that this will definitely work :-)

---

### Post by jonndoe45 on 2009-05-08
Thanks again, last question... honest.

How do I fix grub so that I get rid of the win7 boot option

Tbanks!

---

### Post by kay-man on 2009-05-08
You just delete it from /boot/grub/menu.lst with a text editor

---

### Post by jonndoe45 on 2009-05-09
I have just taken XP/Win7 of my machine for good. Thank you all for your help, it was appreciated. Everything went smoothly with no problems, to be honest, it was damn easy (with the right know how) , thanks again.

One thing I did notice in the Places suubmenu, Filesystem option has disapeared (?) , I can still access it , just the option has gone from the menu.

---

