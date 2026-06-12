---
title: "New Motherboard--No boot?"
date: 2011-07-29
forum: Hardware
---

### Post by jTHEn on 2011-07-29
My ASUS nettop (EB1006) crapped out on me last month and I sent it in for under warranty repair. They said it was the motherboard and replaced it. I got the computer back but it would not boot. It was previously a dual boot with Windows XP. Now, instead of loading GRUB it starts to boot to XP, then fails, and automatically restarts.

I can boot up using the LiveCD and look at my hard drive. My files are still there as far as I can tell. How do I "re-teach" my computer to boot using GRUB?

sudo fsck -l yields:

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xcb5bd2b2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5222    41945683+  17  Hidden HPFS/NTFS
/dev/sda2            5223        5614     3145812    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3           18805       19457     5245222+  1b  Hidden W95 FAT32
/dev/sda4            5614       18804   105951233    5  Extended
Partition 4 does not end on cylinder boundary.
/dev/sda5            5614       18431   102947840   83  Linux
/dev/sda6           18431       18804     3002368   82  Linux swap / Solaris

Partition table entries are not in disk order
```

Any ideas?

Thanks guys!

---

### Post by coffeecat on 2011-07-29
> **jTHEn said:**
> sudo fsck -l yields:

I think you mean "sudo fdisk -l". :)

This is only an educated guess, but it sounds as though the techs have not only replaced the motherboard, but they've re-installed the Windows boot code to the mbr (overwriting grub code) as well, and also that the Windows partition may need repairing. Your fdisk output is a bit odd in that the first NTFS partition (sda1) with the boot flag, and which is approx 43GB, has the hidden flag set as well. That is probably your Windows C: partition because sda2 is far too small for Windows at about 3GB. But I've never seen a hidden Windows C: partition before - I wonder if this is what is preventing Windows from booting.

Whatever, let's have a more detailed overview of your system. Boot up with the Ubuntu live CD and go to this site:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Download and run the boot info script according to the instructions there and post the contents of your RESULTS.txt file in code tags for clarity. At the very least that will show us whether my guess about the mbr is correct and whether grub needs to be re-installed.

---

