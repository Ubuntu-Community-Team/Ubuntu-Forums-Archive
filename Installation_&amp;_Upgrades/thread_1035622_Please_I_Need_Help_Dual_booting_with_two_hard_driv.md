---
title: "Please I Need Help Dual booting with two hard drives"
date: 2009-01-09
forum: Installation &amp; Upgrades
---

### Post by Dragonlive64 on 2009-01-09
Hello -

I am trying to set up my computer to dual boot with Ubuntu and Windows XP. 
In a tutorial I found I was told all I need to do is the following -
-----------------------------------------------------------------------
The problem is that Windows boot must be on the first hard disk/partition in order to boot. You trick it into thinking that by adding those last two lines with the map command in the Grub menu entry. 


(The solution is simply adding this to /boot/grub/menu.lst:)
 
title           Windows XP Professional
root            (hd1,0)
savedefault
makeactive
chainloader     +1
map (hd0) (hd1)
map (hd1) (hd0)

The parts with (hd1,0),(hd0) (hd1) and (hd1) (hd0) depend on where your Windows partition is, which you can find out by typing:

sudo fdisk -l
In this example, Windows is assumed to be on hd1 and Ubuntu on hd0. 
-----------------------------------------------------------------------
Alright, I did that but now I am having problems understanding exactly what that output is telling me! I will paste that output below.....

Disk /dev/sda: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x35ac187e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2327    18691596   83  Linux
/dev/sda2            2328        2434      859477+   5  Extended
/dev/sda5            2328        2434      859446   82  Linux swap / Solaris

Disk /dev/sdb: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xec1bc085

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2327    18691596    7  HPFS/NTFS
/dev/sdb2            2328        2434      859477+   5  Extended
/dev/sdb5            2328        2434      859446   82  Linux swap / Solaris
-------------------------------------------------------------------------

So now I am not sure which hard drive is which, so I can figure out how to use map correctly! I would appreciate any help that you could provide!

Sincerely
J.E. Elmore

---

### Post by Herman on 2009-01-09
Actually, Windows can be located anywhere, in any partition, on any hard drive and boot, if you know how.

If you have Windows in the fist hard drive, there's no need for the 'map' commands.
Grub's 'map' commands help make it easier for most users to boot Windows on a non-first hard drive because that way you don't need to edit Windows /boot.ini file, which is something most people find a little bit scary. 

In most computers you should be able to just run the Ubuntu installer and it will guess the correct hard disk to install the boot loader to and everything will be set up automatically for you.

In a few computers, especially if one hard drive is the IDE type and another is SATA, sometimes the boot loader's pointer gets installed on the wrong MBR by mistake.
If that happens all you need to do is go into your BIOS and switch the hard disks around so the one GRUB was installed to will be the first hard disk. If you do it that way it's very easy and it will be most unlikely that you will need to know any Linux commands or edit any files.

Regards, Herman  :D

---

### Post by Herman on 2009-01-10
```
Disk /dev/sda: 20.0 GB, 20020396032 bytes
 255 heads, 63 sectors/track, 2434 cylinders
 Units = cylinders of 16065 * 512 = 8225280 bytes
 Disk identifier: 0x35ac187e
 
    Device Boot      Start         End      Blocks   Id  System
 /dev/sda1   *           1        2327    18691596   83  Linux
 /dev/sda2            2328        2434      859477+   5  Extended
 /dev/sda5            2328        2434      859446   82  Linux swap / Solaris
 
 Disk /dev/sdb: 20.0 GB, 20020396032 bytes
 255 heads, 63 sectors/track, 2434 cylinders
 Units = cylinders of 16065 * 512 = 8225280 bytes
 Disk identifier: 0xec1bc085
 
    Device Boot      Start         End      Blocks   Id  System
 /dev/sdb1   *           1        2327    18691596    7  HPFS/NTFS
 /dev/sdb2            2328        2434      859477+   5  Extended
 /dev/sdb5            2328        2434      859446   82  Linux swap / Solaris
```:D That looks okay, you have Ubuntu in your first hard disk and Windows in the second hard disk, so you can use the 'map' commands, only put them up higher in the booting stanza, they should come before the 'chainloader' command, because GRUB will run those commands in sequence from the top down, so it's not getting the 'map' commands or it's getting them too late, it has already started booting your Windows boot loader by then.

```
title           Windows XP Professional
root            (hd1,0)
savedefault
makeactive
chainloader     +1
[B]map (hd0) (hd1)
map (hd1) (hd0)[/B]

``````
title           Windows XP Professional
 root            (hd1,0)
[B]map (hd0) (hd1)
  map (hd1) (hd0)[/B]
 savedefault
 makeactive
 chainloader     +1
```

---

