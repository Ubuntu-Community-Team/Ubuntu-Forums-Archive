---
title: "sn9c102 webcam problems"
date: 2005-06-15
forum: Hardware &amp; Laptops
---

### Post by fallscrape on 2005-06-15
I've just done a fresh install of ubuntu.  It is now updated and ready for my devices!

Unfortunately I have not been able to install the webcam - it is a sn9c102 bought from Argos @ 19.99.

It is recognised by the system and did have the drivers install automatically, but a dmesg brings up this:

sn9c102: V4L2 driver for SN9C10x PC Camera Controllers v1:1.19
usb 1-2: SN9C10[12] PC Camera Controller detected (vid/pid 0x0C45/0x602C)
ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
PCI: cache line size of 128 is not supported by device 0000:00:1d.7
ehci_hcd 0000:00:1d.7: USB 2.0 initialized, EHCI 1.00, driver 26 Oct 2004
usb 1-2: No supported image sensor detected
usbcore: registered new driver sn9c102
hub 4-0:1.0: USB hub found
hub 4-0:1.0: 6 ports detected
cpci_hotplug: CompactPCI Hot Plug Core version: 0.2
pci_hotplug: PCI Hot Plug PCI Core version: 0.5
usb 1-2: USB disconnect, address 2
shpchp: shpc_init : shpc_cap_offset == 0
shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
usb 1-2: new full speed USB device using uhci_hcd and address 3
Evaluate _OSC Set fails. Status = 0x0005
pciehp: add_host_bridge: status 5
pciehp: Fails to gain control of native hot-plug
usb 1-2: SN9C10[12] PC Camera Controller detected (vid/pid 0x0C45/0x602C)
usb 1-2: No supported image sensor detected
hw_random: RNG not detected

All of which to me reads 'not working'.

Any ideas on how to fix this?

---

### Post by amex on 2005-11-11
See my post at:
[http://www.ubuntuforums.org/showthread.php?t=49969&page=3&highlight=Video4Linux2]("http://www.ubuntuforums.org/showthread.php?t=49969&page=3&highlight=Video4Linux2")

Maybe it can help you.

---

