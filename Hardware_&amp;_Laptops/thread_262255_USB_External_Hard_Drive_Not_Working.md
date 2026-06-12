---
title: "USB External Hard Drive Not Working"
date: 2006-09-21
forum: Hardware &amp; Laptops
---

### Post by GreySim on 2006-09-21
I have an external USB enclosure for internal IDE hard drives, and it's not mounting or otherwise appearing at all. In Device Manager, it shows up for about 30 seconds, but disappears again. It shows up as:

- USB 2.0 IDE Adapter
--- USB Mass Storage Interface
----- SCSI Host Adapter
--- USB Raw Device Access

From /var/log/messages:

> 
Sep 21 01:02:49 localhost kernel: [ 3045.628235] usb 1-1: new full speed USB device using uhci_hcd and address 16
Sep 21 01:02:53 localhost kernel: [ 3045.769126] scsi3 : SCSI emulation for USB Mass Storage devices
Sep 21 01:03:00 localhost kernel: [ 3056.375799] usb 1-1: reset full speed USB device using uhci_hcd and address 16
Sep 21 01:03:19 localhost kernel: [ 3074.912143] usb 1-1: reset full speed USB device using uhci_hcd and address 16
Sep 21 01:03:37 localhost kernel: [ 3093.448500] usb 1-1: reset full speed USB device using uhci_hcd and address 16
Sep 21 01:03:48 localhost kernel: [ 3103.964145] usb 1-1: reset full speed USB device using uhci_hcd and address 16
Sep 21 01:03:58 localhost kernel: [ 3114.367956] usb 1-1: USB disconnect, address 16
Sep 21 01:03:58 localhost kernel: [ 3114.368129]  3:0:0:0: scsi: Device offlined - not ready after error recovery
Sep 21 01:04:02 localhost kernel: [ 3114.483879] usb 1-1: new full speed USB device using uhci_hcd and address 17
Sep 21 01:04:17 localhost kernel: [ 3133.020158] usb 1-1: new full speed USB device using uhci_hcd and address 18
Sep 21 01:04:35 localhost kernel: [ 3151.556502] usb 1-1: new full speed USB device using uhci_hcd and address 19
Sep 21 01:04:46 localhost kernel: [ 3162.072165] usb 1-1: new full speed USB device using uhci_hcd and address 20


That's after plugging the drive in once, and only once.

---

