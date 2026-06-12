---
title: "USB hub (in LCD monitor) not working properly"
date: 2007-11-04
forum: Hardware &amp; Laptops
---

### Post by teel on 2007-11-04
Hi,
My Dell 2007FP has a built-in USB 2.0 hub. When I connect the monitor usb cable to the computer it seems to be working:

Nov  5 00:18:06 tomek-desktop kernel: usb 3-3: new high speed USB device using ehci_hcd and address 4
Nov  5 00:18:06 tomek-desktop kernel: PM: Adding info for usb:3-3
Nov  5 00:18:06 tomek-desktop kernel: PM: Adding info for No Bus:usbdev3.4_ep00
Nov  5 00:18:06 tomek-desktop kernel: usb 3-3: configuration #1 chosen from 1 choice
Nov  5 00:18:06 tomek-desktop kernel: PM: Adding info for usb:3-3:1.0
Nov  5 00:18:06 tomek-desktop kernel: hub 3-3:1.0: USB hub found
Nov  5 00:18:06 tomek-desktop kernel: hub 3-3:1.0: 4 ports detected
Nov  5 00:18:06 tomek-desktop kernel: PM: Adding info for No Bus:usbdev3.4_ep81
Nov  5 00:18:06 tomek-desktop NetworkManager: <debug> [1194218286.288319] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_424_2504_noserial'). 
Nov  5 00:18:06 tomek-desktop NetworkManager: <debug> [1194218286.366333] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_424_2504_noserial_if0'). 
Nov  5 00:18:06 tomek-desktop kernel: PM: Adding info for No Bus:usbdev3.4
Nov  5 00:18:06 tomek-desktop NetworkManager: <debug> [1194218286.429000] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_424_2504_noserial_usbraw'). 

But when I connect a usb disk drive (which by the way has it's own power and doesn't need one from USB) it is not recognized by the system at all - my syslog/messages is silent about it.

What might be wrong? If the hub is working why does my usb disk fail to start? Under M$ Windows it works ok, so the hardware is ok.

Best regards,
teel

---

