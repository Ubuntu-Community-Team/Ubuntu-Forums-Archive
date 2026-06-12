---
title: "Problem with scanner of Canon MG5750 All-in-one"
date: 2015-11-20
forum: Hardware
---

### Post by jijil on 2015-11-20
Hello,

This is my first post ever in this forum.
I'm from Belgium, frenchspeaking and a happy 2-year user of Linux on my personal PC (only OS installed).

I've  just bought a Canon MG5750 multifunction printer+scanner (in short, I  needed *quickly* a replacement for my dead Epson BX300F, and missed time  to check for linux compatibilty).

It's connected on my Thinkpad T410 laptop, by USB port. OS: Linux Mint 17.2 Cinnamon 64 bits (Debian based, compatible with Ubuntu as long as I know)

The multifunction works perfectly on another Windows PC.

Printer part of this MG5750 works out without problem with Mint.

But  the scanner is not recognized by Sane (including the git version  1.0.26b, compiled on my own, with added libusb library. working with  other devices)
sane-find-scanner sees USB peripherals, including one device for this Canon multifunction,
but scanimage -L doesn't list any working scanner.
(even if I've added "usb 0xAAAA OxBBBB" in /etc/sane.d/pixma.conf, with AAAA et BBBB , vendorID and productID).

Canon  non-free drivers have then been installed (Scangearmp2 v3.20, from  their website). BUT... I get no scanning interface (scan preview). I  just can chose the scanner from a list (it's the only one available) and  the output file (jpg or pdf, but I wish tiff). The scanned result file  is rather poor: the image is like posterized.

Before I'd buy this  MG5750, my father's MG5350 multifunction worked as a charm with Sane  (xsane) and Gutenprint, without any prior specific software/driver  install.

Can you please help me? (either with sane or with scangearmp2)

Thank you by advance [IMG]http://forums.linuxmint.com/images/smilies/icon_smile.gif[/IMG]

---

