---
title: "hdd error:  Result: hostbyte=DID_OK driverbyte=DRIVER_TIMEOUT,SUGGEST_OK"
date: 2009-10-10
forum: Hardware
---

### Post by duzvik on 2009-10-10
I see many repeating error in syslog about hard disk:


Oct 10 09:56:02 s3 kernel: [71800.677482] lost page write due to I/O error on sdd
Oct 10 12:36:12 s3 kernel: [81410.639561] sd 1:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_TIMEOUT,SUGGEST_OK


disk:  1,5Tb SAMSUNG HD154UI

uname -a
Linux s3 2.6.28-15-server #52-Ubuntu SMP Wed Sep 9 11:34:09 UTC 2009 x86_64 GNU/Linux

fdisk -l
 13:03:32: Disk /dev/sdb: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

mount 
/dev/sdb on /home/PATH/1 type xfs (rw)

fsck didn't help

disk plugged to motherboard sata port.
server works without raid.


any ideas?

---

