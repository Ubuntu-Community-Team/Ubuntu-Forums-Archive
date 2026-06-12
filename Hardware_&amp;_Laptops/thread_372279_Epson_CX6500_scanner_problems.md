---
title: "Epson CX6500 scanner problems"
date: 2007-02-28
forum: Hardware &amp; Laptops
---

### Post by CaptainSchnitz on 2007-02-28
I have an Epson Stylus SX6500 printer/scanner which I'm having problems with. Printing works fine, but I can't get the scanner running.

Xsane does not detect the scanner ("No devices available). Investigating this, I found that I needed an additional backend, epkowa, which was included in the libsane-extras package, which I installed through Synaptic. Scanner still not detected when I launch Xsane.

I have also tried installing iscan, but iscan simply reports that it cannot communicate with the scanner.

The only success I have had in getting the system acknowledge the existence of the scanner is with sane-find-scanner, which detects a usb scanner.

Any help with this matter would be greatly appreciated!

---

### Post by CaptainSchnitz on 2007-02-28
Forgot to mention that I am using Edgy Eft.

---

### Post by cornelis1 on 2007-03-01
Try running xsane and iscan as root (gksudo xsane; gksudo iscan).

---

