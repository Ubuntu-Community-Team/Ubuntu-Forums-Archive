---
title: "Epson Stylus SX235W + Ubuntu 15.10 x64"
date: 2016-01-25
forum: Hardware
---

### Post by Tony762 on 2016-01-25
Hi, I have a problem installing my Epson Stylus SX235W via usb. Printing is working but no scanner. I downloaded and installed iscan from epson.
```
sudo sane-find-scanner

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

could not fetch string descriptor: Pipe error
could not fetch string descriptor: Pipe error
could not fetch string descriptor: Pipe error
found USB scanner (vendor=0x04b8, product=0x0885) at libusb:001:006
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.


```

On Ubuntu 13 it worked, but after clean install of 15.10 not.

---

