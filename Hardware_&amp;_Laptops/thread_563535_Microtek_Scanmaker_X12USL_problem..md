---
title: "Microtek Scanmaker X12USL problem."
date: 2007-09-30
forum: Hardware &amp; Laptops
---

### Post by DoktorNo on 2007-09-30
Hi there,

I have an exellent Mikrotek Scanmaker x12 USL scanner (USB/SCSI dual), and this scanner is not working on Ubuntu 7.04, despite thee fact, that it is suppoerted my sane-microtek2 frontend.

lsusb output:
```
Bus 005 Device 002: ID 03f0:7604 Hewlett-Packard 
Bus 005 Device 001: ID 0000:0000  
[COLOR="Red"]Bus 001 Device 002: ID 05da:20b0 Microtek International, Inc. [/COLOR]
Bus 001 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000 
```

sane-find-scanner output:

```
  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.
  # Also you need support for SCSI Generic (sg) in your operating system.
  # If using Linux, try "modprobe sg".

[COLOR="Red"]found USB scanner (vendor=0x05da, product=0x20b0) at libusb:001:002[/COLOR]
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as
  # necessary.
```

Xsane searches for devices, and finds nothing. 

Any ideas? Some time ago, I had this scanner connected via SCSI interface, and it was running well on the Ubuntu Breezy. Now my SCSI card is defunct, so i use USB instead.

---

### Post by linuxwizard on 2007-09-30
On Sane website it shows working Interface is SCSI for that scanner. I don't see anything on USB. If you had it working before on SCSI now you are trying USB and can't get it to work i would say that is your problem.

[http://www.sane-project.org/sane-mfgs.html#Z-MICROTEK](http://www.sane-project.org/sane-mfgs.html#Z-MICROTEK)

---

### Post by DoktorNo on 2007-10-01
The worst thing is, tht my SCSI card (AdvanSys ASC3030) is not working with my motherboard, even on Windows. :(

---

