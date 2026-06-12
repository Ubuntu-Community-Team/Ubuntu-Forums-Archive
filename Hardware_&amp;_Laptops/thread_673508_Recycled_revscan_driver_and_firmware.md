---
title: "Recycled revscan driver and firmware"
date: 2008-01-20
forum: Hardware &amp; Laptops
---

### Post by neilblue on 2008-01-20
Hello,

I have got an old revscan 19200s, which I am trying to get running. I don't have the windows driver disk so I am going at this a little blind. I have read that gt68xx has support for this scanner, and running

> sane-find-scanner

shows that it finds the scanner (I think):
> 
  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x086b, product=0x0104) at libusb:004:004
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as
  # necessary.

Running xsane says no devices found and:

> scanimage -L

Shows:

> No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).

So now I read the man pages and see that I need to add firmware drivers to /usr/share/sane/gt68xx/

But I don't know what the firmware drivers for this device look like. I have opened up a few driver files for windows, but find nothing ending *.usb as suggested by the man pages. Please can anyone tell me first if I am doing the right thing here, and second what the firmware drivers look like.

Thanks
Neil

---

