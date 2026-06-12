---
title: "external hard disk"
date: 2011-03-14
forum: Hardware
---

### Post by sonee on 2011-03-14
Hi everyone,

I have a laptop hard disk in an enclosure and I use it as an external hard disk.
When I plug it in, I check dmesg
```
reset high speed USB device using ehci_hcd and address 3
```After googling I found a solution to solve this problem :
```
echo 64 > /sys/block/sdb/device/max_sectors
```However, it doesn't work if I issue command after the external hard drive is plugged in. It only works if I plug it in, change the value, unplug it, and plug it back in. I cannot change the value before plugging it in because the directory does not exist (it is created after I plug it in).

Is it ok to unplug it when the system is not accessing the hard drive (the light is on but not flashing) ? How can I set the system to automatically set the max_sectors value before it accesses the hard drive ?

Thanks in advance. :p

---

### Post by 07knev on 2011-03-14
I think you need to format your hard drive, to get it recognized

---

### Post by sonee on 2011-03-14
yes, I tried formatting the drive.

Ubuntu DOES recognize the drive, but it is not listed in /dev until I change the max_sectors value. 
After I change max_sectors from 240 (default) to 64, I can mount the drive and use it.

Because /sys/block/sdb/device/max_sectors DOES NOT exist until I plug the hard drive in, I have to plug it in, change the value, unplug it, and plug in again.

---

