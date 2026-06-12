---
title: "Epson Perfection scanner no longer found"
date: 2017-06-02
forum: Hardware
---

### Post by mkapstein on 2017-06-02
When I installed my Epson Perfection 2450 scanner in Ubuntu 16.04 it worked like a charm. Now, suddenly, the computer no longer
finds it at all. I have carefully followed the steps outlined in 
[https://help.ubuntu.com/community/SANE%20-%20Installing%20a%20scanner%20that%20isn%27t%20auto-detected](https://help.ubuntu.com/community/SANE%20-%20Installing%20a%20scanner%20that%20isn%27t%20auto-detected)
to no avail.

On running 
gksudo sane-find-scanner

The response is:
```
  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x0bda [Generic], product=0x0129 [USB2.0-CRW]) at libusb:001:004
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.
```

But the "generic" scanner that is found seems not to correspond to anything at all, certainly
not to my Epson.

Help in resolving the problem would be most appreciated.

---

### Post by slickymaster on 2017-06-02
*Thread moved to **Hardware**.*

---

### Post by mkapstein on 2017-06-04
attempts to detect the scanner have also garnered these responses:

   could not open USB device 0x046d/0xc517 at 002:003: Access denied (insufficient permissions)

 could not open USB device 0x8087/0x0024 at 002:002: Access denied (insufficient permissions)

 could not open USB device 0x1d6b/0x0002 at 002:001: Access denied (insufficient permissions)

 could not open USB device 0x0bda/0x0129 at 001:004: Access denied (insufficient permissions)

 could not open USB device 0x8087/0x0024 at 001:002: Access denied (insufficient permissions)

 could not open USB device 0x1d6b/0x0002 at 001:001: Access denied (insufficient permissions)

---

