---
title: "Sane can't detect HP scanner"
date: 2007-10-17
forum: Hardware &amp; Laptops
---

### Post by Mordac85 on 2007-10-17
I've been trying to get my HP 5370c going but it's driving me nuts.  sane-find-scanner detects the scanner and it shows up in lsusb, but Scanimage -L and Xsane it tell me it can't detect the scanner.

> scanimage -L
No scanners were identified. ...

/usr/bin/sane-find-scanner
found USB scanner (vendor=0x03f0, product=0x0701) at libusb:003:003
I've seen some bugs reported for Feisty, but I'm not sure if this is my problem or something else I'm missing.  Any ideas?

---

### Post by cacycleworks on 2007-12-04
> **Mordac85 said:**
> I've been trying to get my HP 5370c going but it's driving me nuts.  sane-find-scanner detects the scanner and it shows up in lsusb, but Scanimage -L and Xsane it tell me it can't detect the scanner.


I've seen some bugs reported for Feisty, but I'm not sure if this is my problem or something else I'm missing.  Any ideas?

Yes, me too please. I can compile the kernel but can't figure out how to get ubuntu to see the scanner. :P

```
15:15 ~/Desktop$ sane-find-scanner
  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

found USB scanner (vendor=0x03f0, product=0x2405, chip=rts8822L-01H?) at libusb:003:006

```

HP scanjet 4070

---

### Post by saeid on 2008-07-04
same problem

---

