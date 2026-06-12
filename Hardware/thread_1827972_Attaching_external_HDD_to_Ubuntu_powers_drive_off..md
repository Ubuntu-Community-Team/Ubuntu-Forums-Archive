---
title: "Attaching external HDD to Ubuntu powers drive off."
date: 2011-08-18
forum: Hardware
---

### Post by spikeh on 2011-08-18
I have an internal hard drive in an external dock with an USB interface, with the computer running Ubuntu Server 11.04 Natty. If the USB cable from the external dock is not connected to the computer, the drive will power on; on attaching the USB cable the drive will make some seeking noises and then power itself off. I suspect the drive is being put to sleep by Ubuntu?

With the drive in the "powered off" non-spinning state, it is not visible when I invoke "sudo fdisk -l" or "cat /proc/scsi/scsi". However, on inspecting the output from "dmesg", I get this strange log:

```
[  242.852036] usb 1-3: new high speed USB device using ehci_hcd and **address 2**
[  243.057354] usbcore: registered new interface driver uas
[  243.083618] Initializing USB Mass Storage driver...
[  243.083848] scsi2 : usb-storage 1-3:1.0
[  243.085808] usbcore: registered new interface driver usb-storage
[  243.085815] USB Mass Storage support registered.
[  244.088865] scsi 2:0:0:0: Direct-Access     WDC WD20 00JD-00GBB0           PQ: 0 ANSI: 2 CCS
[  244.094787] sd 2:0:0:0: Attached scsi generic sg2 type 0
[  244.327300] sd 2:0:0:0: [sdb] 390721968 512-byte logical blocks: (200 GB/186 GiB)
**[  244.328323] sd 2:0:0:0: [sdb] Write Protect is off**
[  244.328330] sd 2:0:0:0: [sdb] Mode Sense: 34 00 00 00
[  244.328334] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[  244.330725] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[  244.351436]  sdb: sdb1
[  244.353435] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[  244.353528] sd 2:0:0:0: [sdb] Attached SCSI disk
**[  244.459665] usb 1-3: USB disconnect, address 2**
[  249.156035] usb 1-3: new high speed USB device using ehci_hcd and **address 3**
[  249.294665] scsi3 : usb-storage 1-3:1.0
[  250.296824] scsi 3:0:0:0: Direct-Access     WDC WD20 00JD-00GBB0           PQ: 0 ANSI: 2 CCS
[  250.302660] sd 3:0:0:0: Attached scsi generic sg2 type 0
[  250.538633] sd 3:0:0:0: [sdb] 390721968 512-byte logical blocks: (200 GB/186 GiB)
**[  250.539363] sd 3:0:0:0: [sdb] Write Protect is off**
[  250.539368] sd 3:0:0:0: [sdb] Mode Sense: 34 00 00 00
[  250.539373] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[  250.542204] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[  250.562889]  sdb: sdb1
**[  250.563903] usb 1-3: USB disconnect, address 3**
**[  250.564497] sd 3:0:0:0: [sdb] Write Protect is on**
[  250.564503] sd 3:0:0:0: [sdb] Mode Sense: 17 49 f1 af
[  250.564508] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[  250.564596] sd 3:0:0:0: [sdb] Attached SCSI disk

```

Which suggest the drive has successfully mounted. The drive works fine in Windows. I have highlighted some interesting parts of the dmesg log. The drive appears to be assigned to "address 2" with write protection off, disconnect, then be assigned to "address 3" with write protection off, disconnect again, then suddenly write protection turns on? Can someone more knowledgeable please help me go through this log to diagnose the problem?

---

