---
title: "probs w. Epson 4490 scanner after upgrading to 7.10"
date: 2007-10-22
forum: Hardware &amp; Laptops
---

### Post by rziegler72 on 2007-10-22
I'm having issues with my Epson 4490 scanner, after upgrading from 7.04 to 7.10.  It worked fine in 7.04.

I've installed the libsane-extras and sane-utils packages.

sane-find-scanner shows:
found USB scanner (vendor=0x04b8 [EPSON], product=0x0119 [EPSON Scanner]) at libusb:003:002

I added this to /etc/udev/rules.d/45-libsane.rules :
SYSFS{idVendor}=="04b8", SYSFS{idProduct}=="0119", MODE="664", GROUP="scanner"

I added this to /etc/sane.d/epson.conf :
usb 0×04b8 0x0119

Rebooted.  Still no go.  Any ideas or other info I can provide?

Thanks,
~Rick

---

### Post by luca.mg on 2008-02-24
hope this helps [http://ubuntuforums.org/showthread.php?t=705566&highlight=4490](http://ubuntuforums.org/showthread.php?t=705566&highlight=4490) 

ciao luca

---

