---
title: "Inadvertently tried to mount an already mounted partition on a different point."
date: 2009-02-08
forum: Hardware
---

### Post by studout on 2009-02-08
Hi,

I recently added an additional external usb disk.
In the process of updating fstab, I copied the line from the other usb disk, and adjusted the the mount point, but failed to adjust the device from sda1 to sdb1.
When I tried to mount the mount point of the new disk, I was basically trying to mount an already mounted partition on a different point.
mount complained that the special device /dev/sda1 does not exist.  This is the device for the other disk that was already mounted.
This is confirmed by doing "ls /dev/sd <TAB>" and it only shows sdb and sdb1; the new disk.

Here's the relevant dmesg output
```

scsi12 : SCSI emulation for USB Mass Storage devices
usb-storage: device found at 27
usb-storage: waiting for device to settle before scanning
  Vendor: Generic   Model: External          Rev: 1.04
  Type:   Direct-Access                      ANSI SCSI revision: 04
SCSI device sdb: 1953525168 512-byte hdwr sectors (1000205 MB)
sdb: assuming drive cache: write through
SCSI device sdb: 1953525168 512-byte hdwr sectors (1000205 MB)
sdb: assuming drive cache: write through
 sdb: sdb1
sd 12:0:0:0: Attached scsi disk sdb
usb-storage: device scan complete
 0:0:0:0: rejecting I/O to dead device
EXT3-fs error (device sda1): ext3_readdir: directory #2 contains a hole at offset 0
 0:0:0:0: rejecting I/O to dead device
EXT3-fs error (device sda1): ext3_readdir: directory #10829825 contains a hole at offset 0
 0:0:0:0: rejecting I/O to dead device
Buffer I/O error on device sda1, logical block 530
lost page write due to I/O error on sda1
 0:0:0:0: rejecting I/O to dead device
Buffer I/O error on device sda1, logical block 530
lost page write due to I/O error on sda1
 0:0:0:0: rejecting I/O to dead device
Buffer I/O error on device sda1, logical block 530
lost page write due to I/O error on sda1
 0:0:0:0: rejecting I/O to dead device
Buffer I/O error on device sda1, logical block 530
lost page write due to I/O error on sda1
 0:0:0:0: rejecting I/O to dead device
Buffer I/O error on device sda1, logical block 530
lost page write due to I/O error on sda1
 0:0:0:0: rejecting I/O to dead device
Buffer I/O error on device sda1, logical block 530
lost page write due to I/O error on sda1

```
Did I destroy the data on the disk, or is this as simple as usb plug cycling the external disk that is sda?
I decided against simply trying the usb plug cycle at this point, lest I possibly make the situation worse.

Thanks.

---

### Post by studout on 2009-02-08
I fixed the problem.

After I reviewed my logs of what was on that disk, I realized that it would not be *horrible* if the data were lost, so I just did the obvious...

Simply plug cycling the usb cable fixed the problem.  The kernel re-enumerated the disk as sda, I ran fsck.ext3 on it to recover the journal, and remounted it without incident.

ext3 is great; not like the bad old days of ext2.

I suppose that it goes without saying that I fixed the error in made in fstab that caused this in the first place.

Thank you to everyone that looked at my thread.

---

