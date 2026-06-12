---
title: "write access in automount USB mp3"
date: 2007-09-09
forum: Hardware &amp; Laptops
---

### Post by schakravarthi on 2007-09-09
My ubuntu autoloads my mp3 player but doesnt give write acess. although the mtab entry says it is in rw.

I would like to be able to use the autoload feature

/etc/mtab entry after mounting
/dev/sdb1 /media/Sansa\040m230  vfat defaults,user,umask=000 0 0

last few lines of my dmesg.

[81842.139153] sdb: Mode Sense: 00 00 00 00
[81842.139156] sdb: assuming drive cache: write through
[81877.231447] usb 2-1: new full speed USB device using uhci_hcd and address 11
[81877.406852] usb 2-1: configuration #1 chosen from 1 choice
[81877.408907] scsi11 : SCSI emulation for USB Mass Storage devices
[81877.409164] usb-storage: device found at 11
[81877.409168] usb-storage: waiting for device to settle before scanning
[81882.411006] usb-storage: device scan complete
[81882.416005] scsi 11:0:0:0: Direct-Access     SanDisk  Sansa m230       1.30 PQ: 0 ANSI: 0
[81882.469563] SCSI device sdb: 1009664 512-byte hdwr sectors (517 MB)
[81882.553344] sdb: Write Protect is off
[81882.553416] sdb: Mode Sense: 37 00 00 08
[81882.553433] sdb: assuming drive cache: write through
[81882.605111] SCSI device sdb: 1009664 512-byte hdwr sectors (517 MB)
[81882.688062] sdb: Write Protect is off
[81882.688077] sdb: Mode Sense: 37 00 00 08
[81882.688090] sdb: assuming drive cache: write through
[81882.688142]  sdb: sdb1
[81882.697415] sd 11:0:0:0: Attached scsi removable disk sdb
[81882.697825] sd 11:0:0:0: Attached scsi generic sg2 type 0

---

### Post by schakravarthi on 2007-09-09
One more thing. I can write after the automount as root.
 
Its just that I cannot change permissions of the directory and write as user.

---

