---
title: "Samsung multi-function printer C480 - how to get scanner to work"
date: 2018-07-04
forum: Hardware
---

### Post by darthsidious2 on 2018-07-04
The printer is working fine but I can't get any scan program (for example SimpleScan) to recognize a scanner. I have installed ULD from Samsung. It is connected to USB. Any ideas?

> sudo sane-find-scanner 

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.


  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.


found USB scanner (vendor=0x04e8 [Samsung Electronics Co., Ltd.], product=0x347e [C48x Series]) at libusb:001:005
could not fetch string descriptor: Pipe error
could not fetch string descriptor: Pipe error
found USB scanner (vendor=0x0df6 [Manufacturer Realtek ], product=0x0045 [RTL8188S WLAN Adapter ]) at libusb:001:002
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.


  # Not checking for parallel port scanners.


  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.






> scanimage -L

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).




---

### Post by darthsidious2 on 2018-07-05
After too much googling I found this page: [https://wiki.archlinux.org/index.php/SANE/Scanner-specific_problems#Samsung](https://wiki.archlinux.org/index.php/SANE/Scanner-specific_problems#Samsung) 

A simple line 
> usb 0x04e8 0x347e

in xerox_mfp.conf solved the problem.

---

