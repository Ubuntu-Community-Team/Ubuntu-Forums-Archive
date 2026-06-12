---
title: "USB Drive Not Mounting"
date: 2007-04-22
forum: Hardware &amp; Laptops
---

### Post by rivera151 on 2007-04-22
This seems to be a common problem, but I didn want to hijack a thread.  I want to post this output to see if someone who knows better can help.  Here's my dmesg output when I plug in the drive.

```

usb 2-3: new high speed USB device using ehci_hcd and address 5
PM: Adding info for usb:2-3
PM: Adding info for No Bus:usbdev2.5_ep00
usb 2-3: configuration #1 chosen from 1 choice
PM: Adding info for usb:2-3:1.0
scsi3 : SCSI emulation for USB Mass Storage devices
PM: Adding info for No Bus:host3
PM: Adding info for No Bus:usbdev2.5_ep81
PM: Adding info for No Bus:usbdev2.5_ep02
usb-storage: device found at 5
usb-storage: waiting for device to settle before scanning
usb-storage: device scan complete
PM: Adding info for No Bus:target3:0:0
scsi 3:0:0:0: Direct-Access              USB Flash Memory 1.02 PQ: 0 ANSI: 0 CCS
PM: Adding info for No Bus:target3:0:1
PM: Removing info for No Bus:target3:0:1
PM: Adding info for No Bus:target3:0:2
PM: Removing info for No Bus:target3:0:2
PM: Adding info for No Bus:target3:0:3
PM: Removing info for No Bus:target3:0:3
PM: Adding info for No Bus:target3:0:4
PM: Removing info for No Bus:target3:0:4
PM: Adding info for No Bus:target3:0:5
PM: Removing info for No Bus:target3:0:5
PM: Adding info for No Bus:target3:0:6
PM: Removing info for No Bus:target3:0:6
PM: Adding info for No Bus:target3:0:7
PM: Removing info for No Bus:target3:0:7
PM: Adding info for scsi:3:0:0:0
scsi 3:0:0:0: Attached scsi generic sg0 type 0

```

Here's the corresponding lsusb

```

Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 005: ID 0930:653d Toshiba Corp. 
Bus 002 Device 001: ID 0000:0000  

```

I hope this is helpful.

---

