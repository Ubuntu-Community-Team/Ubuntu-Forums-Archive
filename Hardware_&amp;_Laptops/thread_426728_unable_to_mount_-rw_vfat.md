---
title: "unable to mount -rw vfat"
date: 2007-04-28
forum: Hardware &amp; Laptops
---

### Post by pininy on 2007-04-28
Hi,

I'm unable to get the system to auto mount my ext harddisc FAT32, but I am able to do a sudo mount but it does not give me readwrite access, it's only READ-ONLY.

What could be the cause? This disc is able to mount on both my Mac and Windows automatically.

I'm running on 7.04.

many thanks,
thomas


[ 8717.924000] usb 5-1: USB disconnect, address 2
[ 8720.180000] usb 5-2: new high speed USB device using ehci_hcd and address 3
[ 8720.312000] usb 5-2: configuration #1 chosen from 1 choice
[ 8720.312000] scsi8 : SCSI emulation for USB Mass Storage devices
[ 8720.312000] usb-storage: device found at 3
[ 8720.312000] usb-storage: waiting for device to settle before scanning
[ 8725.312000] usb-storage: device scan complete
[ 8725.312000] scsi 8:0:0:0: Direct-Access     ST325082 3A               0000 PQ: 0 ANSI: 0
[ 8725.316000] SCSI device sdb: 488397168 512-byte hdwr sectors (250059 MB)
[ 8725.316000] sdb: Write Protect is off
[ 8725.316000] sdb: Mode Sense: 27 00 00 00
[ 8725.316000] sdb: assuming drive cache: write through
[ 8725.316000] SCSI device sdb: 488397168 512-byte hdwr sectors (250059 MB)
[ 8725.316000] sdb: Write Protect is off
[ 8725.316000] sdb: Mode Sense: 27 00 00 00
[ 8725.316000] sdb: assuming drive cache: write through
[ 8725.316000]  sdb: sdb1
[ 8725.336000] sd 8:0:0:0: Attached scsi disk sdb
[ 8725.336000] sd 8:0:0:0: Attached scsi generic sg1 type 0
[ 8725.776000] UDF-fs: No VRS found
[ 8725.820000] Unable to identify CD-ROM format.

thomas@thomas-laptop:~$ fdisk -l

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30402   244198552+   b  W95 FAT32
thomas@thomas-laptop:~$

---

### Post by taurus on 2007-04-28
Try

```
sudo umount /dev/sdb1
sudo mkdir /media/windows
sudo mount -t vfat /dev/sdb1 /media/windows -o iocharset=utf8,umask=000
ls -la /media
```

---

### Post by pininy on 2007-04-28
thanks, 

it did the trick, hopefully there wud be something that will auto mount it..

appreciated!
:)

---

