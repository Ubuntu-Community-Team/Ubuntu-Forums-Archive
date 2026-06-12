---
title: "Scanner HP f735 not detected"
date: 2013-02-17
forum: Hardware
---

### Post by mbahlol on 2013-02-17
Dear all

I'm using lubuntu 12.10 on my vostro 3450. right now i'm trying to scan using HP Deskjet F735. i've tried simple scan. but the result no scanner detected. i also tried xsane but no device available. using terminal i typed sane-find-scanner and this is what i've got 

> # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

could not open USB device 0x8087/0x0024 at 001:002: Access denied (insufficient permissions)
could not open USB device 0x8087/0x0024 at 002:002: Access denied (insufficient permissions)
could not open USB device 0x1d6b/0x0002 at 001:001: Access denied (insufficient permissions)
could not open USB device 0x1d6b/0x0002 at 002:001: Access denied (insufficient permissions)
could not open USB device 0x1d6b/0x0002 at 003:001: Access denied (insufficient permissions)
could not open USB device 0x1d6b/0x0003 at 004:001: Access denied (insufficient permissions)
could not open USB device 0x138a/0x0011 at 001:004: Access denied (insufficient permissions)
could not open USB device 0x1bcf/0x2b81 at 001:005: Access denied (insufficient permissions)
could not open USB device 0x03f0/0x2904 at 002:007: Access denied (insufficient permissions)
could not open USB device 0x8086/0x0189 at 002:003: Access denied (insufficient permissions)
  # No USB scanners found. If you expected something different, make sure that
  # you have loaded a kernel driver for your USB host controller and have setup
  # the USB system correctly. See man sane-usb for details.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as
  # necessary.


please guide me to solve this problem

Regards

mbahlol

---

### Post by mbahlol on 2013-03-16
after some googling. i found a solutions by instaling Hplip Toolbox from lubuntu software center. and problem solved. must read a lot more

---

