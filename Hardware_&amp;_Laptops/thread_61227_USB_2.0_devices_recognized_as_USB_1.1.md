---
title: "USB 2.0 devices recognized as USB 1.1"
date: 2005-08-30
forum: Hardware &amp; Laptops
---

### Post by jsor on 2005-08-30
My USB 2.0 key drive is being treated as a USB 1.1 device, and the corresponding speed loss is less than desirable.  The USB ports themselves are definitely USB 2.0 (this is on the VIA VT8237R chipset, if that helps).

In usbview, I see five controllers listed so:
```

VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (#4)
VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (#3)
VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (#2)
VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
VIA Technologies, Inc. USB 2.0

```

Any device I attach is assigned to one of the USB 1.1 controllers, even when it apparently sees that the drive is USB 2.0:

```

TD 2C
Manufacturer: Memorex
Speed: 12Mb/s (full)
USB Version:  2.00

```
It notices that the device's USB version is 2.0, but still uses 1.1 for it.

Any ideas why this might be happening?

---

### Post by bionnaki on 2005-08-30
is usb 2.0 enabled in your bios?

---

### Post by nad on 2005-08-30
Look for the EHCI driver in dmesg: dmesg | grep EHCI

If it is not there, you may need to update your system and/or install a newer kernel.

Is 2.0 support enabled in bios?

---

### Post by jsor on 2005-08-31
I looked through the BIOS earlier and the only USB related option seemed to be DOS legacy USB support.  I tried enabling/disabling it anyway with no apparent difference.

Here is the output of dmesg | grep ehci:

```

ehci_hcd 0000:00:10.4: VIA Technologies, Inc. USB 2.0
ehci_hcd 0000:00:10.4: irq 21, pci mem 0xf6000000
ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 5
ehci_hcd 0000:00:10.4: USB 2.0 initialized, EHCI 1.00, driver 26 Oct 2004

```

Also, I forgot to mention earlier, I found and tried a suggestion to add the lines
```

ehci_ucd
uhci_ucd

```
to /etc/modules with the idea to ensure that they are being loaded in the correct order.  It did change the order that they seemed to load at boot time, but it made no difference with my problem.

I'll take a more thorough look in the BIOS.  Thanks for the prompt reply.

---

### Post by nad on 2005-08-31
It may be that the hotplug subsystem is not correctly assigning the bus/handlers.

Try plugging into a diferent port. Use the command: /etc/init.d/hotplug status

Tail your logs after you have plugged the device in.

---

