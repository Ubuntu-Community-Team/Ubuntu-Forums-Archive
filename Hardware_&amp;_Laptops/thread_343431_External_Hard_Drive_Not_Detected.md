---
title: "External Hard Drive Not Detected"
date: 2007-01-21
forum: Hardware &amp; Laptops
---

### Post by lakelovers on 2007-01-21
I have an Iomega 80g external hard drive that worked fine under Dapper until recently. It disappeared from the desktop and it's not accessable. I read most of the posts related to this type problem but could not find a solution for mine. I'm using a USB port on a Dell computer. I have disconnected the USB cable and reconnected using different USB ports which gave me the same response as below. Looking at /media/IOMEGA_HDD, it shows the drive locked and empty, though I can access the drive (or a folder) with Simple Backup Restore but the restore function doesn't work. I'll appreciate your suggestions. 
When I "sudo fdisk -l" this is what I get:


Disk /dev/hda: 30.7 GB, 30750031872 bytes
255 heads, 63 sectors/track, 3738 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3582    28772383+  83  Linux
/dev/hda2            3583        3738     1253070    5  Extended
/dev/hda5            3583        3738     1253038+  82  Linux swap / Solaris

---

