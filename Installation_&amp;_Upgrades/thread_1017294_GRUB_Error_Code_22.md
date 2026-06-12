---
title: "GRUB Error Code 22"
date: 2008-12-20
forum: Installation &amp; Upgrades
---

### Post by OneRingShort on 2008-12-20
I'm trying to install Ubuntu 8.10 x86 on a friend's computer, and I keep running into the same problems.  There are three hard drives, the first one has Windows, and we are trying to install it on the second.  The installation runs smoothly, but when we boot up we get Error 22 on the GRUB boot loader.

We put in the Windows restore disc to restore the Windows boot loaders.  We tried using EasyBCD, but we get "Cannot load from harddisk.  Insert Systemdisk and press any key."  We tried reinstalling GRUB through the liveCD (ala [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)), but we encounter the same error (22).

I've never encountered this error before, and I haven't been able to find much on the subject (outside of restoring the Windows boot loader).

Any help would be greatly appreciated

Matt

P.S. The only thing curious I noticed through out the whole thing, is that when I ran:
```
find /grub/stage1
```
under the liveCD, it output "hd(2,5)", which if I'm not mistaken, is the 6th partition of the 3rd hard drive (We were installing it on the 3rd partition of the second).

---

### Post by cariboo on 2008-12-20
IF you actually are installing Ubuntu on the 3rd partition of the 2nd drive, when you get to the boot menu, highlight Ubuntu and press e then change what ever it is trying to boot from to (hd1,2). Once you have got Ubuntu running set up grub to boot using the blkid of the partition. This is what I have in my /boot/grub/menu.lst:

```
title		Ubuntu jaunty (development branch), kernel 2.6.28-3-generic
uuid		c6afffda-4b72-454e-8bfb-29d122e3cc3e
kernel		/boot/vmlinuz-2.6.28-3-generic root=UUID=c6afffda-4b72-454e-8bfb-29d122e3cc3e ro quiet splash 
initrd		/boot/initrd.img-2.6.28-3-generic
quiet

```

This is actually on the 1st partition of the 2nd hard drive. To find the blkid's of the partitions in a terminal type:

```
blkid
```

Of course you can also see what blkid's the partitions are using by looking at /boot/grub/menu.lst.

Jim

---

### Post by OneRingShort on 2008-12-20
Alright, I think I may have found the problem.  We wanted to install it on the second hard drive on the 3rd partition, but that didn't happen (as the grub list seemed to indicate).  It turns out that Ubuntu saw the SATA2 hard drive as the third disk, and that during the partitioning, some unallocated space was left.  This space forced the swap and the install partition into an extended partition at the end of the disk (explaining the partition number).

I'm running gParted right now to move things around to remove the unallocated space, and I will then try reinstalling Ubuntu.  I'll update when that is finished.

---

### Post by infamous-online on 2008-12-20
Here's what I would do. Since you have 3 harddrives, shut down the pc, unplug your windows os hd and only use the harddrives you wish to install ubuntu on.

Next after the installation is complete shut down your pc. Once the pc is off be sure to plug in your windows os harddrive. Turn on the pc and when the bios screen appears, press whatever button it is to allow you to edit your bios settings and check to see if you can see all three drives. Once that's been confirmed you may need to change to jumpers on your harddrives so ubuntu is the primary drive, and windows being on the cable select a.k.a the second drive. 

Hopefully this approach helps you out.

---

