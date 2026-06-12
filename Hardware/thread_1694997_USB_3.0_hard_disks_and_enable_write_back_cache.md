---
title: "USB 3.0 hard disks and enable write back cache?"
date: 2011-02-25
forum: Hardware
---

### Post by Signal64 on 2011-02-25
With 10.04.1 I'm getting less than 40MBs write speed on two usb 3.0 drives but getting decent read speeds on both.

I noticed in dmesg that the drive cache is being set as write through.

From dmesg```
[  267.676207] usb 5-1: new SuperSpeed USB device using xhci_hcd and address 2
[  267.693777] xhci_hcd 0000:02:00.0: WARN: short transfer on control ep
[  267.694151] xhci_hcd 0000:02:00.0: WARN: short transfer on control ep
[  267.694526] xhci_hcd 0000:02:00.0: WARN: short transfer on control ep
[  267.695027] xhci_hcd 0000:02:00.0: WARN: short transfer on control ep
[  267.695231] usb 5-1: configuration #1 chosen from 1 choice
[  267.705478] Initializing USB Mass Storage driver...
[  267.705675] scsi6 : SCSI emulation for USB Mass Storage devices
[  267.705829] usb-storage: device found at 2
[  267.705832] usb-storage: waiting for device to settle before scanning
[  267.705851] usbcore: registered new interface driver usb-storage
[  267.705855] USB Mass Storage support registered.
[  272.704427] usb-storage: device scan complete
[  272.704828] scsi 6:0:0:0: Direct-Access     WD       My Book 1130     1012 PQ: 0 ANSI: 6
[  272.705159] scsi 6:0:0:1: Enclosure         WD       SES Device       1012 PQ: 0 ANSI: 6
[  272.705643] sd 6:0:0:0: Attached scsi generic sg3 type 0
[  272.705772] scsi 6:0:0:1: Attached scsi generic sg4 type 13
[  285.369621] sd 6:0:0:0: [sdd] 732558336 4096-byte logical blocks: (3.00 TB/2.72 TiB)
[  285.369778] sd 6:0:0:0: [sdd] Write Protect is off
[  285.369780] sd 6:0:0:0: [sdd] Mode Sense: 47 00 10 08
[  285.369783] sd 6:0:0:0: [sdd] Assuming drive cache: write through
[  285.370104] sd 6:0:0:0: [sdd] 732558336 4096-byte logical blocks: (3.00 TB/2.72 TiB)
[  285.370262] sd 6:0:0:0: [sdd] Assuming drive cache: write through
[  285.370266]  sdd: sdd1
[  285.379510] sd 6:0:0:0: [sdd] 732558336 4096-byte logical blocks: (3.00 TB/2.72 TiB)
[  285.379845] sd 6:0:0:0: [sdd] Assuming drive cache: write through
[  285.379851] sd 6:0:0:0: [sdd] Attached SCSI disk
[  285.415200] ses 6:0:0:1: Attached Enclosure device
[  285.439954] xhci_hcd 0000:02:00.0: WARN: Stalled endpoint
```

Read speed for both drives using hdparm -Tt /dev/sdd1:```

wd my book
/dev/sdd1:
 Timing cached reads:   13266 MB in  1.99 seconds = 6666.76 MB/sec
 Timing buffered disk reads:  376 MB in  3.00 seconds = 125.16 MB/sec

seagate goflex
/dev/sdd1:
 Timing cached reads:   13328 MB in  1.99 seconds = 6697.37 MB/sec
 Timing buffered disk reads:  444 MB in  3.00 seconds = 147.85 MB/sec
```

Is there any way to enable write back cache?
hdparm doesn't work with usb devices.

---

