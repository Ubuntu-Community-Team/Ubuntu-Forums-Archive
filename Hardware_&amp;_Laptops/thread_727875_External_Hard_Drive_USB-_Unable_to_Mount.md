---
title: "External Hard Drive USB- Unable to Mount"
date: 2008-03-18
forum: Hardware &amp; Laptops
---

### Post by Brian10 on 2008-03-18
Brand New to Linux - Please Help


I have not been able to mount my Maxtor External Hard Drive (USB) .  I know the drive works because I just tested it on a Windows Machine and no problem.  When I first tried Ubuntu off of the CD Boot Version it seemed to work fine.  A month later when I found the time to make a permanent installation I have not been able to mount.  The system recognizes the ext drive and I can see it from My Computer.  Please HELP...  This is the result of sudo fdisk -l.   thanks for any advice .  All of the commands I have tried have not been successful.  I have read through all the relevant posts.



 Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf4d64506

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9327    74919096   83  Linux
/dev/hda2            9328        9729     3229065    5  Extended
/dev/hda5            9328        9729     3229033+  82  Linux swap / Solaris

Disk /dev/sda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x65ba2f70

---

### Post by taurus on 2008-03-18
> **Brian10 said:**
> 

Disk /dev/sda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x65ba2f70

There is nothing after the Disk identifier?

What's the output of this command from a terminal?

```
dmesg | tail
```
When you connect the external drive to a windows machine, make sure you eject it or unmount it from a computer instead of just unplugging it.

---

