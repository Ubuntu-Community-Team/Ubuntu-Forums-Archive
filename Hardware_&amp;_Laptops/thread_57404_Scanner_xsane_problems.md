---
title: "Scanner xsane problems"
date: 2005-08-16
forum: Hardware &amp; Laptops
---

### Post by lesliem on 2005-08-16
Hi all,
Having problems getting my usb 240TH DIRECT WEBSCAN GOLD scanner to work.
Ubuntu seems to recognise it as another make [Mustek] during boot. However can't get any related software to operate it. Tried the following and read Sane page regarding gt68xx backend, but no joy yet. Would appreciate any help.

# sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x055f, product=0x021a [USB Scanner], chip=GT-6816) at libusb:004:002
found USB scanner (vendor=0x08ca, product=0x0103) at libusb:002:002
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.
  # scanimage -L
device `gt68xx:libusb:004:002' is a Mustek BearPaw 2448 TA Plus flatbed scanner

Thanks all

---

