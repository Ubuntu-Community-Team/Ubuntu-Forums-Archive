---
title: "Problem in boot up Ubuntu from a USB drive"
date: 2008-10-09
forum: General Help
---

### Post by yinglcs2 on 2008-10-09
Hi,

I have following this tutorial to setup ubuntu 8.04 from usb drive.
[http://www.pendrivelinux.com/2008/04/14/ubuntu-804-usb-hard-drive-install/](http://www.pendrivelinux.com/2008/04/14/ubuntu-804-usb-hard-drive-install/)

I have having problem boot the ubuntu from usb drive.
What i am seeing is
1. my laptop tries to boot from the usb drive
2. it said 'Starting'
3. It fails and says 'Error loading 17'

I never see the screen which let me to choose to boot from 'Ubuntu 8.04'
or 'Ubuntu 8.04 (recovery mode), etc, etc.

Can you please tell me how can I fix my problem?

Thank you.

---

### Post by WWSmith36 on 2008-10-09
Grub error 17 : Cannot mount selected partition

This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB.  There are a few different things that can cause this

Please Boot to LiveCD and open a terminal from the menu Applications-> Accessories-> Terminal and type this command and post its output

```
sudo fdisk -lu
```

---

### Post by yinglcs2 on 2008-10-10
Thank you.

Here is a weird thing I notice.
I get error 17 when I boot straight from the usb drive (installed with ubuntu 8.04)

But if I 
* boot from my internal hard drive (i have ubuntu 7.10 install) by pulling out the usb drive
* mount the usb drive after I boot up from the internal hard drive (by just clicking the drive icon in 'Computer' in the file manaage)
* restart my computer in (this time with usb drive pulled in)

This way, it boots up.
I can't understand why, but it works for some reason. I try this multiple times.

Here is the command output:

```

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders, total 195371568 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xed1f86f7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    61432559    30716248+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2        61432560   185968439    62267940    f  W95 Ext'd (LBA)
Partition 2 does not end on cylinder boundary.
/dev/sda3       185976000   195365519     4694760   12  Compaq diagnostics
Partition 3 does not end on cylinder boundary.
/dev/sda5       155252223   155461004      104391   83  Linux
/dev/sda6       155461068   185968439    15253686   83  Linux
/dev/sda7        61432686    90783314    14675314+  83  Linux
/dev/sda8        90783378    95667074     2441848+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders, total 117210240 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x44e4be6d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63     4883759     2441848+  82  Linux swap / Solaris
/dev/sdb2         4883760    64468844    29792542+  83  Linux
/dev/sdb3        64468845   117210239    26370697+  83  Linux

Disk /dev/sdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000326

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63    58653314    29326626   83  Linux
/dev/sdc2        58653315    62557109     1951897+  82  Linux swap / Solaris
/dev/sdc3        62557110    80839079     9140985   83  Linux
/dev/sdc4        80839080   144327959    31744440   83  Linux


```

Thank you for any help.

---

### Post by yinglcs2 on 2008-10-10
/dev/sdb1 is where I have my ubuntu 8.0.4 installed in the usb drive.

---

### Post by caljohnsmith on 2008-10-10
> **yinglcs2 said:**
> 
Here is a weird thing I notice.
I get error 17 when I boot straight from the usb drive (installed with ubuntu 8.04)

But if I 
* boot from my internal hard drive (i have ubuntu 7.10 install) by pulling out the usb drive
* mount the usb drive after I boot up from the internal hard drive (by just clicking the drive icon in 'Computer' in the file manaage)
* restart my computer in (this time with usb drive pulled in)

This way, it boots up.
I can't understand why, but it works for some reason. I try this multiple times.
I certainly don't understand either why your above technique would fix your Grub error 17. You might want to change some of your BIOS settings related to your USB drive and see if that changes anything; I would recommend writing down any BIOS settings you change so you can easily revert back if necessary. Let us know if you come up with any more clues about your USB drive's strange behavior, or if you find the problem. :)

---

### Post by yinglcs2 on 2008-10-10
This 'trick' has been working for multiple times. 
I don't know why either. This USB drive is brand new. And after I boot from the USB drive , it runs fine.

As far as update BIOS setting, I don't know what should I set to.

---

