---
title: "External usb sata drive stop being detected"
date: 2009-03-10
forum: Hardware
---

### Post by picha on 2009-03-10
I have an 2.5 sata drive in an external case that connects trough usb.
This used to work fine, but last time a plug-it in it wasn't detected, e suspect that there is something wrong with the drive or the case, but I'm not sure.

the dmesg detects the drive but noting more (like size or partitions):
```

[  560.612262] usb 7-2: new high speed USB device using ehci_hcd and address 3
[  560.748585] usb 7-2: configuration #1 chosen from 1 choice
[  560.749835] scsi3 : SCSI emulation for USB Mass Storage devices
[  560.750822] usb-storage: device found at 3
[  560.750832] usb-storage: waiting for device to settle before scanning
[  565.748581] usb-storage: device scan complete
[  565.749682] scsi 3:0:0:0: Direct-Access     USB TO I DE/SATA Device   0002 PQ: 0 ANSI: 0
[  565.754116] sd 3:0:0:0: [sdb] Attached SCSI disk
[  565.755228] sd 3:0:0:0: Attached scsi generic sg2 type 0

```

Whats your do you think, is it gone for good or it's still salvageable in an easy way.


PS: By the way, i wave the same problem on windows with the drive. So it's is clearly not a Linux problem.

---

