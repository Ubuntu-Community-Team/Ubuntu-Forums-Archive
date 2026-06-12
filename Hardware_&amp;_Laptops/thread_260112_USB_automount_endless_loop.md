---
title: "USB automount endless loop"
date: 2006-09-18
forum: Hardware &amp; Laptops
---

### Post by mohrt on 2006-09-18
Hello,

I'm having a problem with automounting a USB drive. I'm using a USB adapter for a Sony Duo Pro camera memory card.

When I plug in the USB device, I get this in dmesg output:

```
[17407749.748000] usb 4-4: new high speed USB device using ehci_hcd and address 30
[17407749.880000] scsi510 : SCSI emulation for USB Mass Storage devices
[17407749.884000] usb-storage: device found at 30
[17407749.884000] usb-storage: waiting for device to settle before scanning
[17407751.524000] usb 4-4: USB disconnect, address 30
[17407751.764000] usb 4-4: new high speed USB device using ehci_hcd and address 31
[17407751.896000] scsi511 : SCSI emulation for USB Mass Storage devices
[17407751.900000] usb-storage: device found at 31
[17407751.900000] usb-storage: waiting for device to settle before scanning
[17407753.540000] usb 4-4: USB disconnect, address 31
[17407753.780000] usb 4-4: new high speed USB device using ehci_hcd and address 32
[17407753.912000] scsi512 : SCSI emulation for USB Mass Storage devices
[17407753.912000] usb-storage: device found at 32
[17407753.912000] usb-storage: waiting for device to settle before scanning
[17407755.556000] usb 4-4: USB disconnect, address 32
```


This loop goes endlessly.

I'm using Dapper with the latest updates. pmount shows I'm using version 0.9.11. I have confirmed that this drive mounts on a Mac OS X laptop and the images are viewable, so the card is good.

Thanks for any help!

---

