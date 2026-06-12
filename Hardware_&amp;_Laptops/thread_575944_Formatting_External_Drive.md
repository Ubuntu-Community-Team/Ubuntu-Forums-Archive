---
title: "Formatting External Drive"
date: 2007-10-14
forum: Hardware &amp; Laptops
---

### Post by Max Luebbe on 2007-10-14
I recently got a cheap external IDE enclosure from EBay and want to use it to hold a 80gb drive I've got for doing some backups via rsync.

When I plug the drive in and turn it on, it doesn't get mounted. Here is what dmesg provides:

```
[53484.208000] usb 5-3: new high speed USB device using ehci_hcd and address 3
[53484.388000] usb 5-3: configuration #2 chosen from 1 choice
[53484.896000] usbcore: registered new interface driver libusual
[53484.912000] Initializing USB Mass Storage driver...
[53484.916000] scsi2 : SCSI emulation for USB Mass Storage devices
[53484.916000] usbcore: registered new interface driver usb-storage
[53484.916000] USB Mass Storage support registered.
[53484.916000] usb-storage: device found at 3
[53484.916000] usb-storage: waiting for device to settle before scanning
[53489.916000] usb-storage: device scan complete
[53495.528000] usb 5-3: reset high speed USB device using ehci_hcd and address 3
[53505.788000] usb 5-3: reset high speed USB device using ehci_hcd and address 3
[53511.048000] usb 5-3: reset high speed USB device using ehci_hcd and address 3
[53521.308000] usb 5-3: reset high speed USB device using ehci_hcd and address 3
[53521.456000] scsi 2:0:0:0: scsi: Device offlined - not ready after error recovery

```

What should I start troubleshooting first?
I also have no idea what the current partition table on this drive looks like.

Thanks.

---

### Post by Max Luebbe on 2007-10-14
Anyone have any ideas?

---

