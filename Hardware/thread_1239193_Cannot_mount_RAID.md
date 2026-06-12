---
title: "Cannot mount RAID"
date: 2009-08-13
forum: Hardware
---

### Post by jdfr on 2009-08-13
Ok - 1st post here as although a total linux newb I installed a machine I built with hardy a few months ago and with only a few forum lookups got it all working as I wanted with not much issue and has run nicely ever since.  I have installed a couple of disks that are running in RAID 0 and that was being shown as 1000gb media in hardy.

It was mounting to a folder called Media.  Anyway,I re-booted after an update recently and now it does not want to boot (though the updates are prob a red-herring)  Now it gives me a message 'Invalid mount option when attempting to mount volume' - this is when I click on the 1000gb Media icon that still shows.

How can I fix this please? (I know that I could adjust mount permissions in the right click gui but can't access that now and don't know much at all about the cmd line access - sorry!)

Hope someone can help!
Thanks

Edit:  P.S.  results of fdisk -l...  (smaller drives - 1st raid set - still working well)

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000a984f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18662   149902483+  fd  Linux raid autodetect
/dev/sda2           18663       19457     6385837+   5  Extended
/dev/sda5           18663       19457     6385806   fd  Linux raid autodetect

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0006553c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       18662   149902483+  fd  Linux raid autodetect
/dev/sdb2           18663       19457     6385837+  fd  Linux raid autodetect

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0006f32c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1      121601   976760001   fd  Linux raid autodetect

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000e04ca

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1      121601   976760001   fd  Linux raid autodetect

Disk /dev/md0: 153.5 GB, 153500057600 bytes
2 heads, 4 sectors/track, 37475600 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table

Disk /dev/md2: 6538 MB, 6538985472 bytes
2 heads, 4 sectors/track, 1596432 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x00000000

Disk /dev/md2 doesn't contain a valid partition table

Disk /dev/md1: 1000.2 GB, 1000202174464 bytes
2 heads, 4 sectors/track, 244189984 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x00000000

Disk /dev/md1 doesn't contain a valid partition table

---

