---
title: "Dell USB hard disk  not getting recognized in Ubuntu 11.10"
date: 2013-01-10
forum: Hardware
---

### Post by jamesbon on 2013-01-10
I have a Dell USB hard disk 1 TB and it does not gets detected in Ubuntu 11.10 64 bit , this hard disk is working in Windows ,
but when I attach it to USB port I do not see it in Nautilus (left hand pane) and neither do I see any thing in lsusb corresponding to hard disk.
Here is dmesg output when the hard disk was attached to Ubuntu 11.10 64 bit

```

[   81.640043] usb 2-1: new high speed USB device number 3 using ehci_hcd
[   81.774506] scsi8 : uas
[   81.775818] scsi 8:0:0:0: Direct-Access     Dell     USB Portable HDD 040D PQ: 0 ANSI: 6
[   87.808241] scsi 8:0:0:0: uas_eh_abort_handler tag 0
[   87.808252] scsi 8:0:0:0: uas_eh_device_reset_handler tag 0
[   87.808257] scsi 8:0:0:0: uas_eh_target_reset_handler tag 0
[   87.808261] scsi 8:0:0:0: uas_eh_bus_reset_handler tag 0
[   87.920248] usb 2-1: reset high speed USB device number 3 using ehci_hcd
[   88.053287] scsi 8:0:0:0: Device offlined - not ready after error recovery
[   88.053315] scsi 8:0:0:0: rejecting I/O to offline device
[   88.053325] scsi 8:0:0:0: rejecting I/O to offline device
[   88.054431] scsi 8:0:0:1: Direct-Access     Dell     USB Portable HDD 040D PQ: 0 ANSI: 6
[   88.055555] scsi 8:0:0:2: Direct-Access     Dell     USB Portable HDD 040D PQ: 0 ANSI: 6
[   88.056682] scsi 8:0:0:3: Direct-Access     Dell     USB Portable HDD 040D PQ: 0 ANSI: 6
[   88.057806] scsi 8:0:0:4: Direct-Access     Dell     USB Portable HDD 040D PQ: 0 ANSI: 6
[   88.058930] scsi 8:0:0:5: Direct-Access     Dell     USB Portable HDD 040D PQ: 0 ANSI: 6
[   88.060112] scsi 8:0:0:6: Direct-Access     Dell     USB Portable HDD 040D PQ: 0 ANSI: 6
[   88.061174] scsi 8:0:0:7: Direct-Access     Dell     USB Portable HDD 040D PQ: 0 ANSI: 6
[   88.061390] sd 8:0:0:0: Attached scsi generic sg2 type 0
[   88.061538] sd 8:0:0:1: Attached scsi generic sg3 type 0
[   88.061675] sd 8:0:0:2: Attached scsi generic sg4 type 0
[   88.061810] sd 8:0:0:3: Attached scsi generic sg5 type 0
[   88.061933] sd 8:0:0:4: Attached scsi generic sg6 type 0
[   88.062065] sd 8:0:0:5: Attached scsi generic sg7 type 0
[   88.062197] sd 8:0:0:6: Attached scsi generic sg8 type 0
[   88.062327] sd 8:0:0:7: Attached scsi generic sg9 type 0

```

What can I do so that this hard disk gets detected and I can work with it in Ubuntu 11.10 (64 bit)

---

