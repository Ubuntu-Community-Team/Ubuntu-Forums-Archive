---
title: "Kubuntu not picking up external hard drive."
date: 2007-06-17
forum: Hardware &amp; Laptops
---

### Post by truckinharry on 2007-06-17
Im posting this because in a previous install ubuntu picked up on my external 40g hard drive. I installed kubuntu and it only pickes up on my 2g thumb drive not my 40g external. searched dmesg and came up with this. 

[   16.740000] SCSI device sdb: 78140160 512-byte hdwr sectors (40008 MB)
[   16.740000] sdb: Write Protect is off
[   16.740000] sdb: Mode Sense: 27 00 00 00
[   16.740000] sdb: assuming drive cache: write through
[   16.744000] SCSI device sdb: 78140160 512-byte hdwr sectors (40008 MB)
[   16.744000] sdb: Write Protect is off
[   16.744000] sdb: Mode Sense: 27 00 00 00
[   16.744000] sdb: assuming drive cache: write through
[   16.744000]  sdb:<5>sd 1:0:0:0: Attached scsi generic sg0 type 0
[   16.772000] sd 0:0:0:0: Attached scsi generic sg1 type 0
[   17.236000]  sdb1
[   17.236000] sd 0:0:0:0: Attached scsi disk sdb
[ 1373.512000] VFS: Can't find ext3 filesystem on dev sdb.
[ 1373.512000] VFS: Can't find a valid FAT filesystem on dev sdb.


I understand its not a FAT filesystem but why is this a problem in this install? and is there a way i can make kubuntu mount it like a usb drive should be.

Thanks for your help in advance.
Truckinharry

---

### Post by mikesignguy on 2007-06-17
is it a ntfs drive?

---

