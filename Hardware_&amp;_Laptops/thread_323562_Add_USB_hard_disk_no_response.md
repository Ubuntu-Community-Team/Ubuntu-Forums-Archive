---
title: "Add USB hard disk no response"
date: 2006-12-22
forum: Hardware &amp; Laptops
---

### Post by moonhk on 2006-12-22
I try to add USB hard disk, the system no response. The USB hard disk and USB port are OK.

root@HEX:/media# fdisk -l

Disk /dev/hda: 20.5 GB, 20576747520 bytes
255 heads, 63 sectors/track, 2501 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2420    19438618+  83  Linux
/dev/hda2            2421        2501      650632+   5  Extended
/dev/hda5            2421        2501      650601   82  Linux swap / Solaris

Disk /dev/sda: 16 MB, 16384000 bytes
4 heads, 16 sectors/track, 500 cylinders
Units = cylinders of 64 * 512 = 32768 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         500       15979+   1  FAT12
root@HEX:/media#


root@HEX:/media# uname -a
Linux HEX 2.6.15-26-server #1 SMP Thu Aug 3 04:09:15 UTC 2006 i686 GNU/Linux
root@HEX:/media#

---

### Post by scrooge_74 on 2006-12-22
Question: is that of those external USB HD?  You want to use it as an extra disk or backup disk? 

Or are you trying to boot from it?

When in your desktop you plugged in it doesn't appear on your desktop?

---

### Post by moonhk on 2006-12-22
External USB HD for Data disk not for booting. 

When plugged in the system. It doesnot appear on my desktop.

---

### Post by Nephrolithiasis on 2006-12-22
i have a USB flash disc that is not picked up on inserting - any suggestions?

---

### Post by scrooge_74 on 2006-12-22
I just read this in another thread may give some light to the problem

[http://ubuntuforums.org/showthread.php?t=323504](http://ubuntuforums.org/showthread.php?t=323504)

---

