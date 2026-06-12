---
title: "External USB hard drive not working"
date: 2006-07-23
forum: Hardware &amp; Laptops
---

### Post by The Belgain on 2006-07-23
I'm trying to use an external USB hard drive in Dapper on an Acer laptop, but it's not appearing when I plug it in.  Dmesg shows the following output when the drive is plugged in:

```
[17200770.848000] usb 4-4: new high speed USB device using ehci_hcd and address 2
[17200771.848000] ehci_hcd 0000:00:10.3: Unlink after no-IRQ?  Controller is probably using the wrong IRQ.
[17200782.392000] usb 4-4: device not accepting address 2, error -110
[17200782.504000] usb 4-4: new high speed USB device using ehci_hcd and address 3
[17200794.048000] usb 4-4: device not accepting address 3, error -110
[17200794.160000] usb 4-4: new high speed USB device using ehci_hcd and address 4
[17200804.584000] usb 4-4: device not accepting address 4, error -110
[17200804.696000] usb 4-4: new high speed USB device using ehci_hcd and address 5

```

Any idea what might be causing this?  Lspci shows the following info about my USB controllers:

```
0000:00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
0000:00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
0000:00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
0000:00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)

```

Help would be much appreciated...

---

