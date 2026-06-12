---
title: "iPod v1.2.1 problems"
date: 2007-02-14
forum: Hardware &amp; Laptops
---

### Post by bhartsock on 2007-02-14
I just updated my iPod to version 1.2.1 and started having problems mounting it on linux.  The mount occurs fine when I plug it up, but it now mounts as a read-only filesytem.  It worked prior to this update and is very boggling.

I have tried chmod-ing it with no luck (can't modifiy a read-only filesystem)

Here is the dmesg output:

```

[17185741.540000] usb 2-9: new high speed USB device using ehci_hcd and address 8
[17185741.672000] usb 2-9: configuration #1 chosen from 2 choices
[17185741.676000] scsi12 : SCSI emulation for USB Mass Storage devices
[17185741.676000] usb-storage: device found at 8
[17185741.676000] usb-storage: waiting for device to settle before scanning
[17185746.676000] usb-storage: device scan complete
[17185746.676000]   Vendor: Apple     Model: iPod              Rev: 1.62
[17185746.676000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17185746.680000] SCSI device sdb: 58605119 512-byte hdwr sectors (30006 MB)
[17185746.680000] sdb: Write Protect is off
[17185746.680000] sdb: Mode Sense: 68 00 00 08
[17185746.680000] sdb: assuming drive cache: write through
[17185746.688000] SCSI device sdb: 58605119 512-byte hdwr sectors (30006 MB)
[17185746.688000] sdb: Write Protect is off
[17185746.688000] sdb: Mode Sense: 68 00 00 08
[17185746.688000] sdb: assuming drive cache: write through
[17185746.688000]  sdb: sdb1 sdb2
[17185746.720000] sd 12:0:0:0: Attached scsi removable disk sdb
[17185746.720000] sd 12:0:0:0: Attached scsi generic sg1 type 0
[17185746.948000] printk: 17 messages suppressed.
[17185746.948000] Buffer I/O error on device sdb2, logical block 29222232
[17185746.948000] Buffer I/O error on device sdb2, logical block 29222233
[17185746.948000] Buffer I/O error on device sdb2, logical block 29222234
[17185746.948000] Buffer I/O error on device sdb2, logical block 29222232
[17185746.948000] Buffer I/O error on device sdb2, logical block 29222233
[17185746.948000] Buffer I/O error on device sdb2, logical block 29222234
[17185746.952000] Buffer I/O error on device sdb2, logical block 29222234
[17185746.956000] Buffer I/O error on device sdb2, logical block 29222234
[17185746.956000] Buffer I/O error on device sdb2, logical block 29222234
[17185746.956000] Buffer I/O error on device sdb2, logical block 29222234
[17185747.356000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[17185761.296000] FAT: Filesystem panic (dev sdb2)
[17185761.296000]     invalid access to FAT (entry 0x6774ea32)
[17185761.296000]     File system has been set read-only

```

There is about 50 more filesystem panics.

Any help would be greatly appreciated.

---

### Post by bhartsock on 2007-02-25
Fixed:

If you select "Manage my own library" option from iTunes it completely fixes this problem.

---

### Post by Nephiel on 2007-03-09
I have checked "Manually manage..." on iTunes and still get those buffer IO errors on dmesg.
```
[44320124.300000] usb 4-3: new high speed USB device using ehci_hcd and address 20
[44320124.450000] usb 4-3: configuration #1 chosen from 2 choices
[44320124.450000] scsi18 : SCSI emulation for USB Mass Storage devices
[44320124.450000] usb-storage: device found at 20
[44320124.450000] usb-storage: waiting for device to settle before scanning
[44320129.450000]   Vendor: Apple     Model: iPod              Rev: 1.62
[44320129.450000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[44320129.450000] SCSI device sda: 14651279 2048-byte hdwr sectors (30006 MB)
[44320129.450000] sda: Write Protect is off
[44320129.450000] sda: Mode Sense: 68 00 00 08
[44320129.450000] sda: assuming drive cache: write through
[44320129.450000] SCSI device sda: 14651279 2048-byte hdwr sectors (30006 MB)
[44320129.460000] sda: Write Protect is off
[44320129.460000] sda: Mode Sense: 68 00 00 08
[44320129.460000] sda: assuming drive cache: write through
[44320129.460000]  sda: sda1 sda2
[44320129.460000] sd 18:0:0:0: Attached scsi removable disk sda
[44320129.460000] sd 18:0:0:0: Attached scsi generic sg0 type 0
[44320129.470000] usb-storage: device scan complete
[44320129.590000] printk: 139 messages suppressed.
[44320129.590000] Buffer I/O error on device sda2, logical block 14603084
[44320129.590000] Buffer I/O error on device sda2, logical block 14603084
[44320129.590000] Buffer I/O error on device sda2, logical block 14603084
[44320129.590000] Buffer I/O error on device sda2, logical block 14603084
[44320129.590000] Buffer I/O error on device sda2, logical block 14603084
[44320129.590000] Buffer I/O error on device sda2, logical block 14603084
```

---

### Post by barney_1 on 2007-04-17
I have the same errors.  Have read that building your own kernel with EFI disabled has fixed this issue for some.

Does anyone have a less drastic fix for this problem?

---

