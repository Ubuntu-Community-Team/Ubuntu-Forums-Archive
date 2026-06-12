---
title: "external hdd problems unable to browse some folders"
date: 2007-01-27
forum: Hardware &amp; Laptops
---

### Post by roniez on 2007-01-27
Yea basiclly i got a extarnal hdd from trekstor that uses 2 usb slots.
i plug it in and it functions perfectly on some folders but not some.
i get a io error in dmesg.

> [17261856.140000] usb 4-4: new high speed USB device using ehci_hcd and address 8
[17261856.176000]  1:0:0:0: rejecting I/O to dead device
[17261856.272000] usb 4-4: configuration #1 chosen from 1 choice
[17261856.272000] scsi7 : SCSI emulation for USB Mass Storage devices
[17261856.272000] usb-storage: device found at 8
[17261856.272000] usb-storage: waiting for device to settle before scanning
[17261856.324000]  1:0:0:0: rejecting I/O to dead device
[17261856.472000]  1:0:0:0: rejecting I/O to dead device
[17261856.620000]  1:0:0:0: rejecting I/O to dead device
[17261856.768000]  1:0:0:0: rejecting I/O to dead device
[17261856.916000]  1:0:0:0: rejecting I/O to dead device
[17261857.064000]  1:0:0:0: rejecting I/O to dead device
[17261857.216000]  1:0:0:0: rejecting I/O to dead device
[17261857.364000]  1:0:0:0: rejecting I/O to dead device
[17261857.516000]  1:0:0:0: rejecting I/O to dead device
[17261857.664000]  1:0:0:0: rejecting I/O to dead device
[17261857.812000]  1:0:0:0: rejecting I/O to dead device
[17261857.960000]  1:0:0:0: rejecting I/O to dead device
[17261858.108000]  1:0:0:0: rejecting I/O to dead device
[17261858.256000]  1:0:0:0: rejecting I/O to dead device
[17261858.404000]  1:0:0:0: rejecting I/O to dead device
[17261858.552000]  1:0:0:0: rejecting I/O to dead device
[17261858.700000]  1:0:0:0: rejecting I/O to dead device
[17261858.848000]  1:0:0:0: rejecting I/O to dead device
[17261858.996000]  1:0:0:0: rejecting I/O to dead device
[17261859.148000]  1:0:0:0: rejecting I/O to dead device
[17261859.296000]  1:0:0:0: rejecting I/O to dead device


Any ideas?

---

### Post by allwin on 2007-01-27
> **roniez said:**
> Yea basiclly i got a extarnal hdd from trekstor that uses 2 usb slots.
i plug it in and it functions perfectly on some folders but not some.
i get a io error in dmesg.



Any ideas?

I get this same thing a lot.  I got one high speed drive which connects via USB 2.0, mounts on the desktop and all that, but five seconds later, I get about the same errors.

This would be about my fifth "me too" post.  The other threads never attracted anyone with a suggestion how to fix it.  I'll be listening in hopes someone knows something we can do this time!

---

### Post by allwin on 2007-01-27
[http://bugme.osdl.org/show_bug.cgi?id=4057]("http://bugme.osdl.org/show_bug.cgi?id=4057")

Looks like we are not alone.  USB hard drive enclosures seem to be one of those things that just "don't work" in Linux.  Granted this thread is not so close to our particular problems, but you can see the morass of crud going on even with other distros.  Depressing.

---

