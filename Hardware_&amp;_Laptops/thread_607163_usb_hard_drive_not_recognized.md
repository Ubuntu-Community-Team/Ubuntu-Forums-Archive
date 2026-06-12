---
title: "usb hard drive not recognized"
date: 2007-11-08
forum: Hardware &amp; Laptops
---

### Post by wsx123 on 2007-11-08
ubuntu 7.10,my usb hard drive is not showing up or mounting.The usb port works with other devices and the hard drive works under windows XP.I had it as NTFS, reformatted to FAT32 and still won't show up.

---

### Post by Giradman on 2007-11-08
Yes, I've been having the same problem - I have an older (3+ yrs) Transcend StoreJet (20 GB) USB HD - used it on an XP laptop w/o a problem, but I cannot consistently see this drive on a new Dell LP running VISTA nor on my old IBM ThinkPad now running Ubuntu 7.1 - sent my 3rd e-mail to Transcend - no VISTA or Linus drivers listed on their website - doubt that a positive answer will be provided from them!

But I'm hoping that the 'hardware guru's' reading this thread might have a answer for this problem - e.g. some generic driver or other solution?  :(

BTW - I also have a new Iomega 160 GB Red EGO (shown below) - slick little & fast USB HD - this one is recognized readily in VISTA & also on the old IBM w/ Ubuntu! :)

[IMG]http://www.iomega.com/media/direct/images/products/image_detail_gray/det_ego_red_keyg_fae3.jpg[/IMG]

---

### Post by taurus on 2007-11-08
Plug in your external harddrive.  Then, open a terminal and post the output of this command here.

Applications -> Accessories -> Terminal
```
sudo fdisk -l  <-- lower case letter l, not number 1
```

---

### Post by Giradman on 2007-11-08
> **taurus said:**
> Plug in your external harddrive.  Then, open a terminal and post the output of this command here.

Applications -> Accessories -> Terminal
```
sudo fdisk -l  <-- lower case letter l, not number 1
```

**Taurus** - thanks for your prompt response! :)  Quoted below is the output you requested; however, tonight when I plugged in the Transcend StoreJet, Unbuntu recognized the drive & put an icon on the desktop!  This afternoon, I swear that I plugged it in 3x or more w/ NO recognition - very frustrating - Transcend has not responded, so not sure 'what' to do w/ this external USB drive except to use it on just XP systems (or give it away?) -  thanks for any comments or advice - :KS

> Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       19077    19534832    b  W95 FAT32
david@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 20.0 GB, 20003880960 bytes
255 heads, 63 sectors/track, 2432 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0007390c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2342    18812083+  83  Linux
/dev/sda2            2343        2432      722925    5  Extended
/dev/sda5            2343        2432      722893+  82  Linux swap / Solaris

Disk /dev/sdb: 20.0 GB, 20003749888 bytes
64 heads, 32 sectors/track, 19077 cylinders
Units = cylinders of 2048 * 512 = 1048576 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       19077    19534832    b  W95 FAT32
david@ubuntu:~$ 


---

### Post by wsx123 on 2007-11-09
I have a dual install with open suse 10.3, below is what shows up-only my 20gb harddrive.

[sudo] password for manny:

Disk /dev/sda: 20.0 GB, 20003880960 bytes
255 heads, 63 sectors/track, 2432 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00017810

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1243     9984366   83  Linux
/dev/sda2            2273        2432     1285200    5  Extended
/dev/sda3   *        1244        2272     8265442+  83  Linux
/dev/sda5            2326        2432      859446   82  Linux swap / Solaris
/dev/sda6            2273        2325      425659+  82  Linux swap / Solaris

Partition table entries are not in disk order
manny@manny-laptop:~$

---

### Post by wsx123 on 2007-11-16
Anyone?
My USB hard drive is still not working  but the powerlight is on after I did a fresh 7.10 install.

---

### Post by taurus on 2007-11-16
And what's the output of that same command again?

```
sudo fdisk -l
```

---

### Post by wsx123 on 2007-11-16
manny@manny-laptop:~$ sudo fdisk -l
[sudo] password for manny:

Disk /dev/sda: 20.0 GB, 20003880960 bytes
255 heads, 63 sectors/track, 2432 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000951fb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2325    18675531   83  Linux
/dev/sda2            2326        2432      859477+   5  Extended
/dev/sda5            2326        2432      859446   82  Linux swap / Solaris
manny@manny-laptop:~$

---

### Post by taurus on 2007-11-16
Still not showing up.  What about 

```
dmesg | tail
```

---

### Post by wsx123 on 2007-11-16
manny@manny-laptop:~$ dmesg | tail
[ 2113.604000] usb 2-1: reset full speed USB device using uhci_hcd and address 15
[ 2114.280000] usb 2-1: device descriptor read/64, error -71
[ 2115.656000] usb 2-1: reset full speed USB device using uhci_hcd and address 15
[ 2116.332000] usb 2-1: device descriptor read/64, error -71
[ 2117.324000] usb 2-1: reset full speed USB device using uhci_hcd and address 15
[ 2118.000000] usb 2-1: device descriptor read/64, error -71
[ 2119.380000] usb 2-1: reset full speed USB device using uhci_hcd and address 15
[ 2120.056000] usb 2-1: device descriptor read/64, error -71
[ 2121.308000] hub 2-0:1.0: over-current change on port 1
[ 2121.428000] usb 2-1: reset full speed USB device using uhci_hcd and address 15
manny@manny-laptop:~$

---

### Post by wsx123 on 2007-11-16
I also have a floppy 1 showing up under places>computer showing 14.4 GB free space?
I have no floppy drive.

---

