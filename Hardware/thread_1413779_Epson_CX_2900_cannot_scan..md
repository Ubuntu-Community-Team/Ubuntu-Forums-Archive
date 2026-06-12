---
title: "Epson CX 2900 cannot scan."
date: 2010-02-22
forum: Hardware
---

### Post by JakcV on 2010-02-22
I am currently using ubuntu 9.10 64 bit. I can't scan with Xsane. The Xsane detect the /dev/video0 as the webcam at my laptop. When used sane-find-scanner, it detect my scanner.
```

found USB scanner (vendor=0x04b8, product=0x0830) at libusb:005:004
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

```

In last year, while I was still using Hardy Heron ubuntu 8.04, I can use XSane to scane after install the libsane-extras.

---

### Post by ellgor on 2010-02-23
Hi, 

Go to the "Avasys" site, its for Epson's, and get their Imagescan package (get the deb package as its easier to install with gdebi) works after a reboot.

Regards, Ellgor.

---

### Post by JakcV on 2010-02-25
Thanks. The problem is solved. However, the printer driver can't be used in 64-bit environment. 
I am confused that why sane can't detect the printer anymore like the old version?

---

