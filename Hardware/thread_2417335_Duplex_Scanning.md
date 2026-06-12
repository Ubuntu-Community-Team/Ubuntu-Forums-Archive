---
title: "Duplex Scanning"
date: 2019-04-22
forum: Hardware
---

### Post by mobeustech on 2019-04-22
My issue is that the program is not scanning both sides of my documents.  I have looked at the preferences and it is set to scan both sides.  This is from the ADF tray.  I am guessing that I am missing something somewhere in a config file maybe but I have no idea where to start.

Newly installed system with a Samsung M3870FW

Operating System: Ubuntu 18.10
  Kernel: Linux 4.18.0-17-generic
  Architecture: x86-64
Sane: 1.0.14-13 amd64[FONT=monospace]
[/FONT]Simple-Scan: 3.30.1.1

It is found with running sane-find-scanner and scanimage -L

```
sudo sane-find-scanner

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x04e8 [Samsung Electronics Co., Ltd.], product=0x3460 [M337x 387x 407x Series]) at libusb:001:003
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.
```

scanimage -L produces a lot of OID notices (I have attached the output) but at the bottom of it is:

```
device `xerox_mfp:libusb:001:003' is a Samsung M337x 387x 407x Series multi-function peripheral
```

---

