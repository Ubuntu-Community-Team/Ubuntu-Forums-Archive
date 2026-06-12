---
title: "fsck died with exit status 3"
date: 2007-05-28
forum: Hardware &amp; Laptops
---

### Post by Michelpt on 2007-05-28
Hi everyone, please, need help in this question>

after I did fsck I can not boot from HDD, because during the boot I have this message 

 > /dev/hda3 contains a file system errors, checked forced. [failed]. fsck died with exit status 3 
Then pc was rebooted automatically and do fsck again during the boot and fails with the same status 3. I can not even boot from hard disk.
 However, when I boot Live CD I can mount and read and write to /dev/hda3 which is my ext3 root and home partition. 
 Anybody knows how to fix this problem? Thanx in advance for your help.

---

### Post by Michelpt on 2007-05-28
If it will be useful info I post the outputs of my disk mapping here:

> ubuntu@ubuntu:~$ sudo fdisk -l /dev/hda

Disk /dev/hda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3280    26346568+   7  HPFS/NTFS
/dev/hda2            3281        3408     1028160   82  Linux swap / Solaris
/dev/hda3            3409       12161    70308472+  83  Linux


> ubuntu@ubuntu:~$ sudo fdisk -l /dev/hda3

Disk /dev/hda3: 71.9 GB, 71995875840 bytes
16 heads, 63 sectors/track, 139500 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

Disk /dev/hda3 doesn't contain a valid partition table
ubuntu@ubuntu:~$ 

---

### Post by nidelius on 2007-08-20
Hi!

I have a similair problem. I installed Win Vista then Kubuntu. after playing around for a while for some reason I made a fsck on the Vista partition when I was in KDE Kubuntu. After rebooting I get the same message like you also it reboots and the same procedure again. I attach a photo on the screen how it looks.

```

fsck 1.40-WIP (14-Now-2006)
/dev/hda2: Superblovk last write time is in the future. FIXED.
/dev/hda2 contains a file system with errors, check forced.
/dev/hda2: ***** REBOOT LINUX *****
/dev/hda2: 150980/2970340 files (1.2% non-contiguous), 5425543/5938025 blocks
fsck died with exit status 3
                                                                [FAIL]
 * The file system check corrected errors on the root partition but requested that the system be restarted.
 * The system will be restarted in 5 seconds.

```

There must be a way to boot with the Live CD and then remove the fsck check or repair the error. PLEASE if someone know how to do this I would be very happy if you could post :D

---

### Post by cuspidis on 2008-01-24
Hello, i had the same problem, due to a power shutdown.
try this turnarond : 
- in Bios set system clock to the past (i.e. xx/yy/1999) 
- start ubuntu (it should boot)
- you should be prompted to change system time (s.o. suspects that something is wrong), anyway reboot system and change again system clock in bios, now to the correct date.
- start ubuntu and everything should be ok

i did not investigate further, for lack of time, but it worked.

---

