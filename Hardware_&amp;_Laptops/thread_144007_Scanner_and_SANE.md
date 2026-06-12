---
title: "Scanner and SANE"
date: 2006-03-13
forum: Hardware &amp; Laptops
---

### Post by BorgHunter on 2006-03-13
I am having trouble scanning with my Brother MFC-420CN scanner. I am getting some conflicting results...
```
$ sudo sane-find-scanner

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a SCSI driver for your SCSI adapter.
  # Also you need support for SCSI Generic (sg) in your operating system.
  # If using Linux, try "modprobe sg".

found USB scanner (vendor=0x04f9, product=0x0162) at libusb:001:002
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.
```
```
$ sudo scanimage -L

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).
```
XSane agrees with scanimage. Pressing the Scan button has no effect. And I remember the scanner working just fine in the past, but it does not seem to be working any longer. I'd rather not reboot to Windows to scan my document...

---

