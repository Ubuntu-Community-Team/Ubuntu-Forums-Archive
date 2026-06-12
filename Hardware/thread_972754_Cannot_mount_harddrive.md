---
title: "Cannot mount harddrive"
date: 2008-11-06
forum: Hardware
---

### Post by rypicken on 2008-11-06
I currently have two harddrives running on my pc. One with strictly ubuntu and the other with strictly vista. Until the last update I was allowed to access the vista HD through ubuntu. Now when I try to access it tells me "Cannot mount harddrive". I want to be able to pull some music from the other HD without altering the HD and still being able to boot into vista or ubuntu.


sudo fdisk -l
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe2ed28d4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18701   150215751   83  Linux
/dev/sda2           18702       19457     6072570    5  Extended
/dev/sda5           18702       19457     6072538+  82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x025b4137

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       19458   156288000    7  HPFS/NTFS




Thank You

---

### Post by wouterspace on 2008-11-06
Yah had a similar thing happening but with XP

try adding "-o force" to the end of your mount command

try it

---

