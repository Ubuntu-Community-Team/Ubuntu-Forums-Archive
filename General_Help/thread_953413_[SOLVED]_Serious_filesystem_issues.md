---
title: "[SOLVED] Serious filesystem issues"
date: 2008-10-20
forum: General Help
---

### Post by eyefragment on 2008-10-20
Earlier today, I accidentally booted into Gateway's recovery partition on my laptop.  Once I realized what was going on, I figured that I would let it finish booting, and then tell it that my machine was perfectly fine, and no, I did not, in fact, want anything recovered.  This appeared to work, but upon booting, I now receive a GRUB error 22.

I've tried the reinstall tutorials that involve using a liveCD (I have one for Hardy 8.04 x64)and running sudo grub, find /stage1 or variants thereof, and the find command is never able to find anything.  I have also looked at gparted, and here's where I become scared. 

My windows partitions are untouched, and running happily.  /dev/sda4, where my linux partitions were, is not such a pretty sight. Subpartition /dev/sda5 is supposed to be my swap, but instead has an unknown filesystem and a little warning sign next to it (presumably signifying the "unknown" filesystem).  What used to be /dev/sda6 is unallocated.  My boot flag also appears to now be on my windows partition.  I don't recall if it used to be that way, but switching the flag over to /dev/sda4 doesn't fix my problems.

Running sudo fdisk -l Yields:
Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk indentifier:  0xd13572af

Device      boot  [omitted start, end, Blocks] ID   System
/dev/sda1                                      27   Unknown
/dev/sda2    *                                 7    HPFS/NTFS
/dev/sda3                                      7    HPFS/NTFS
/dev/sda4                                      5    Extended
/dev/sda5                                      82   Linux swap / Solaris

In any case, I'm pretty sure that the recovery partition didn't have enough time to actually delete (m)any files, only edit the partition tables.  Why did it decide to mutilate my linux install?  I have no idea, but I desperately need it back.  Thanks in advance for the help.

---

### Post by macheboy on 2008-10-20
Try with booting from windows install disk and then selecting the recovery console.
There type:
```
fdisk /mbr
```
That should fix it.

---

### Post by eyefragment on 2008-10-20
I booted my windows install disk, but there was no "recovery console" option.  Vista just had two options:  "Fix my Computer" and "install windows vista."  I would have tried "Fix my Computer," hoping that it would drop me to a command line where I could fdisk, but I've had bad experiences (like, say, the one that lead me into this mess) with windows style software modifying thing without explicitly asking for permission, so I wasn't about to ask vista to "fix my computer" and hope that it would be more specific about what it was doing on the next screen.  Thus, I'm still at square one.  Thanks for the reply though!

---

### Post by macheboy on 2008-10-20
You could try to get Windows XP disk. I thing there (on the blue screen) you have to press R.
I don't know how to help you more.

Good luck.

---

### Post by az on 2008-10-20
It may have simply changed your partition table without actually doing anything to the data on the partitions themselves.  You can use parted to "rescue" lost partitions or use Testdisk to do it.  Run them from the live cd.

If you can remember the approximate size and location of your linux partition and swap, you can delete the current entries in the partition table and add the correct values back using the above tool(s)

---

### Post by eyefragment on 2008-10-20
Parted wasn't able to find the partition, but testdisk got it!  I need to do a bit of fiddling with grub to make ubuntu boot again (I'm getting error 17 now), but I can see all of my files!

In particular, I now have my LaTeX'd algebra homework that's due in 2 hours back.  Thank you so much!  You're a lifesaver.

---

