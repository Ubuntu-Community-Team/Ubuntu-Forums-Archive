---
title: "USB Device Failure"
date: 2005-02-07
forum: Hardware &amp; Laptops
---

### Post by jak on 2005-02-07
A strange error occurs for my USB memory stick.
From dmesg:
```

sdb : READ CAPACITY failed.
sdb : status=0, message=00, host=7, driver=00
sdb : sense not available.
sdb: Write Protect is off
sdb: Mode Sense: 00 00 00 00
sdb: assuming drive cache: write through
sdb : READ CAPACITY failed.
sdb : status=0, message=00, host=7, driver=00
sdb : sense not available.
sdb: Write Protect is off
sdb: Mode Sense: 00 00 00 00
sdb: assuming drive cache: write through
 /dev/scsi/host4/bus0/target0/lun0:<3>Buffer I/O error on device sdb, logical bl ock 0
Buffer I/O error on device sdb, logical block 0
 unable to read partition table

```

This is repeated again and again and again.....
Just after I switch my computer on, USB works and the longest time I guess is about 30 mins before plugging in a USB device (not just memory sticks) doesnt work. The USB device recieves no power. I've had to keep restarting to get it running again.

This is from dmesg when it works:
```

Attached scsi removable disk sdb at scsi1, channel 0, id 0, lun 0
USB Mass Storage device found at 9
SCSI device sdb: 512000 512-byte hdwr sectors (262 MB)
sdb: Write Protect is off
sdb: Mode Sense: 03 00 00 00
sdb: assuming drive cache: write through
SCSI device sdb: 512000 512-byte hdwr sectors (262 MB)
sdb: Write Protect is off
sdb: Mode Sense: 03 00 00 00
sdb: assuming drive cache: write through
 /dev/scsi/host1/bus0/target0/lun0: p1

```
Any help?

---

