---
title: "very slow printing (possible usb problem)"
date: 2007-09-25
forum: Hardware &amp; Laptops
---

### Post by elsaturnino on 2007-09-25
I have a Brother MFC-240C which I installed and got working using the driver provided by Brother. It works fine but the printing is horribly slow (maybe a page a minute on a good day :) ). Oddly enough, the scanner in this device works at the normal speed.

I looked on this forum and noticed one other person was dealing with slow printing with this model of printer. Like him, my device ends up using USB 1.0 rather than the 2.0 rated speed. Could this be what is causing the slow printing?

After starting up the printer dmsg gives me the following message:

```

[33092.039972] usb 5-2.4: new full speed USB device using ehci_hcd and address 21
[33092.133462] usb 5-2.4: configuration #1 chosen from 1 choice
[33092.134381] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 21 if 0 alt 0 proto 2 vid 0x04F9 pid 0x01AB
[33092.134864] scsi10 : SCSI emulation for USB Mass Storage devices
[33092.135055] usb-storage: device found at 21
[33092.135057] usb-storage: waiting for device to settle before scanning
[33097.128932] usb-storage: device scan complete
[33097.162769] scsi 10:0:0:0: Direct-Access     Brother  MFC-240C         1.00 PQ: 0 ANSI: 2
[33097.203070] sd 10:0:0:0: Attached scsi removable disk sdb
[33097.203142] sd 10:0:0:0: Attached scsi generic sg1 type 0

```

lsusb says that the device is using USB 1.0, which it shouldn't be. If I plug my USB HDD into the same USB port, it says it is USB 2.0 so I don't think it's a problem with the port.

Any idea why it won't show up as USB 2.0?

---

### Post by racepics on 2007-09-26
I too have very slow printing. Over 44 minutes for one A4 photo!!
Printer is Epson CX6500 on USB2.0 interface. 
I can print a test page in less than one minute - but a A4 photo on high quality takes 44+ minutes to print from Gimp :(
The same thing printed from Win2K to the same printer takes 4min
The print-head is not stopping or pausing it sounds like normal printing but takes forever...
I'm using Ubuntu64 - 7.04
Driver is "High Quality Image (Gutenprint CUPS) (expert)" according to the printer properties.

---

