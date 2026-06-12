---
title: "[SOLVED] Reinstalling Windows"
date: 2008-08-18
forum: General Help
---

### Post by +Eric on 2008-08-18
I'm going to be reinstalling windows here, hopefully tonight. I originally installed vista, then ubuntu on my machine but since have not booted up vista. I know that it has gone back it's time to be activated, and I don't really want to deal with that or deal with vista for that matter.

I want to install xp, but want to have a solid plan in place so I don't mess with anything. I'm fairly new to linux and use it exclusively on both my desktop and my laptop, so I just want to make sure I'm doing everything right and don't screw up my linux installation.

Warhammer online is coming out soon and I want to prepare to play it. :)

```
eric@Raven:~$ sudo fdisk -l
[sudo] password for eric: 

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe830e830

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38914   312568832    7  HPFS/NTFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38156   306488038+  83  Linux
/dev/sdb2           38157       38913     6080602+   5  Extended
/dev/sdb5           38157       38913     6080571   82  Linux swap / Solaris

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       42360   340250977    7  HPFS/NTFS
/dev/sdc2           42360       60802   148132864    7  HPFS/NTFS

Disk /dev/sdd: 2063 MB, 2063597056 bytes
255 heads, 63 sectors/track, 250 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x91f72d24

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1         251     2015200    7  HPFS/NTFS
Partition 1 has different physical/logical endings:
     phys=(249, 254, 63) logical=(250, 225, 38)
```It's fairly clear, but /dev/sda is my windows drive, /dev/sdb is Linux, /dev/sdc is a data drive and sdd1 is just my plugged in thumb drive.

I plan on just formatting sda like I would normally to install windows, but I realize this is going to remove grub. I plan on following [this guide]("http://ubuntuforums.org/showthread.php?t=224351&highlight=reinstall+grub") to reinstall grub, but it does worry me a bit since I've never done it. Losing my ubuntu install would not be the end of the world since the important stuff from there is backed up, just a lot of hassle to get my video card and sound working again.... not to mention getting everything the way I want it.

So, just wanted to make sure I had nothing really to worry about or I wasn't missing something and that my plan was solid. Pretty sure I'm gtg, but I know I'm new!

The grub install does worry me a bit, however I know from my past experience that while things may not seem so clear when you look at them, when you actually get to doing it, it all falls into place and makes sense.

So any advice would be greatly appreciated!

---

### Post by caljohnsmith on 2008-08-18
I wouldn't worry one bit about overwriting Grub--if Grub is in the sda MBR it will get overwritten by installing Windows XP, but it is as simple as following that guide you linked to in order to put Grub back in the MBR. Not a big deal at all. :)

---

### Post by +Eric on 2008-08-18
Cool, since I'm realtively new, I just wanted confirmation I wasn't missing something that would finish me off #-olol.

---

