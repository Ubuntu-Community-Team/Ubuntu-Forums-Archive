---
title: "I can zero a 250gb sata drive, but I cannot format. Anybody know why?"
date: 2009-08-12
forum: Hardware
---

### Post by ddixonr on 2009-08-12
A friend on mine asked to reinstall his OS for him. The plan was to do a Ubuntu/XP dual boot. He left his HDD but not his computer. Unfortunately, my desktop died, so I cannot install the HDD into an actual desktop. I did, however, perform a $ sudo dd if=/dev/zero of=/dev/sdb on the drive to be doubly sure nothing was left. I am using a sata-usb adapter. It always works great, so I don't believe it is to blame.

Upon trying to format I get errors. Cannot create new filesystem. Any filesystem- I tried them all.

Is there something physically wrong the drive, or is this something I did. BTW, this drive did have multiple viruses, and wouldn't boot. Inserting a Live Ubuntu cd took an incredibly long time to boot in the original computer, and wouldn't get past 5% during the install.

Edit: Since I started with zero partitions, I created one using the entire drive selecting the unformatted option when it asked what file system to use with the new partition. After applying those selections, I selected format using NTFS and it worked. I hope this wasn't a fluke and the hard drive won't die suddenly later.

---

### Post by doas777 on 2009-08-12
something may be wrong with the drive. does gparted/'fdisk -l' see it?

---

### Post by ddixonr on 2009-08-12
Oh yeah, everything looks fine until I start the format. Like I said, the zeroing worked fine without any errors, so it pops up in the system fine.

---

### Post by doas777 on 2009-08-12
how does the drive look in SMART?
[https://help.ubuntu.com/community/Smartmontools](https://help.ubuntu.com/community/Smartmontools)

---

### Post by ddixonr on 2009-08-12
```
ryan@Ub-laptop:~$ sudo fdisk -l

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x27fb27fa

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            1218       12161    87907680    5  Extended
/dev/sda2   *           1        1217     9775521   83  Linux
/dev/sda5           11913       12161     2000092+  82  Linux swap / Solaris
/dev/sda6            1218       11911    85899492   83  Linux

Partition table entries are not in disk order

Disk /dev/mmcblk0: 16.0 GB, 16071000064 bytes
218 heads, 56 sectors/track, 2571 cylinders
Units = cylinders of 12208 * 512 = 6250496 bytes
Disk identifier: 0x00000000

        Device Boot      Start         End      Blocks   Id  System
/dev/mmcblk0p1               1        2572    15690240    6  FAT16

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00045e39

   Device Boot      Start         End      Blocks   Id  System
ryan@Ub-laptop:~$ sudo smartctl -a -d ata /dev/sdb
smartctl version 5.38 [i686-pc-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

Smartctl: Device Read Identity Failed (not an ATA/ATAPI device)

A mandatory SMART command failed: exiting. To continue, add one or more '-T permissive' options.
ryan@Ub-laptop:~$ 

```

Is there a USB option?

Edit: I tried --all /dev/sdb and it said the drive does not support self test logging.

---

### Post by dandnsmith on 2009-08-12
If you zeroed the drive, as you said, then you **cannot** format until you've created a partition table with at least one partition!

Use anything you like - fdisk, gparted ...

---

### Post by kerry_s on 2009-08-12
i agree once you zero it, you have to unplug & plug it back in so it can be reread, no icon should show up when you plug it in, just open gparted & it will tell you when you go to format it.

---

