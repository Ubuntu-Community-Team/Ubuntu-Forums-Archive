---
title: "[ask]how to do, my scanner doesn detect"
date: 2008-04-02
forum: Hardware &amp; Laptops
---

### Post by benquick on 2008-04-02
help me, my scanner doesnot detect
Brand: Microtek ScanMaker 3880

this is my resuslt #sane-find-scanner

# sane-find-scanner will now attempt to detect your scanner. If the
# result is different from what you expected, first make sure your
# scanner is powered up and properly connected to your computer.

# No SCSI scanners found. If you expected something different, make sure that
# you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x05da [Prolific Technology Inc.], product=0x3021 [USB Scanner ], chip=SQ113) at libusb:004:008
# Your USB scanner was (probably) detected. It may or may not be supported by
# SANE. Try scanimage -L and read the backend's manpage.

# Not checking for parallel port scanners.

# Most Scanners connected to the parallel port or other proprietary ports
# can't be detected by this program.

and result scanimagae #scanimage -L

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).

help me, how to do to resolve my trouble?

---

### Post by K.Mandla on 2008-04-02
Moved to Hardware and Laptops.

---

### Post by benquick on 2008-06-15
none else reply or gimme suggestion to my thread, maybe I must throw my scanner to trash:(:mad:

---

### Post by Sularco on 2008-06-29
Support for the SQ113 chip through Sane is yet in its infancy. The only device with that chip currently under development is the Mustek BearPaw 2448 TA Pro - check its current status at 

[http://www.sane-project.org/snapshots/](http://www.sane-project.org/snapshots/)

and look for the mustek_usb2 backend.

Like with many low-end devices support through Sane will most likely remain limited and disposing of your device and replacing it for one with full support on the Sane device listing might be a viable idea.

---

