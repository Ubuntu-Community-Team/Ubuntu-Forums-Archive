---
title: "Printer epson cx 5600"
date: 2009-05-03
forum: Hardware
---

### Post by fsancho05 on 2009-05-03
Hi guys, I'm having a trouble with my printer, the functions of the printer works normally, and I just plug it in usb port and ubuntu recognized, but I can not use the scanner, how can I do you to install the scanner of my printer.

Pardon my english!

Thanks!!!

---

### Post by Dark_Stang on 2009-05-03
You will want to have xsane installed to use your scanner. My last epsion AIO worked "out of the box" with xsane.

---

### Post by fsancho05 on 2009-05-05
Hi, thanks for the answer, but I already have the Xsane, and the Xsane doens't recognize no one dispositives.

Thanks!

---

### Post by bootdoc on 2009-05-08
having same issue with epson cx7450.  Have xsane and libsane-extras installed.  sudo sane-find-scanner gives this:

found USB scanner (vendor=0x04b8, product=0x0838) at libusb:002:009
found USB scanner (vendor=0x0bda, product=0x8187 [RTL8187_Wireless_LAN_Adapter]) at libusb:002:003

The first being the epson printer scanner.  scanimage -L gives this:

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).

---

