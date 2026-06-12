---
title: "Permissions problem with xsane and HP scanner"
date: 2010-07-25
forum: Hardware
---

### Post by mkozlov on 2010-07-25
I am trying to use my HP ScanJet 5200C scanner which is connected through USB. I am using sane to detect it and have installed xsane as a graphical frontend. When I run xsane I get the error message "no devices available". However when I run xsane as root I get a big warning message say this operation is DANGEROUS. Having skipped this warning I was able to scan a document. **Was wondering what I need to do to make xsane work without root access?**

P.S. After running xsane as root my chromium browser tells me that it cannot access preferences on startup.:(
```
max@max-desktop:/$ lsusb
Bus 005 Device 003: ID 03f0:0401 Hewlett-Packard ScanJet 5200c
...

```
```
max@max-desktop:/$ sane-find-scanner

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

**found USB scanner (vendor=0x03f0, product=0x0401) at libusb:005:003**
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as
  # necessary.

```

---

### Post by stoobers on 2011-09-01
I have this same problem.

I haven't found a solution yet.

The scanner seems to work sporadically regardless of whether I am root or not.

---

