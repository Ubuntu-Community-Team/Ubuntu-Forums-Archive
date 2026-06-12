---
title: "I have one problem with my scanner"
date: 2007-04-28
forum: Hardware &amp; Laptops
---

### Post by uranus0206 on 2007-04-28
i have a scanner : BENQ S2W 3300U
and i did the steps on SANE website 

the command : sane-find-scanner

found USB scanner (vendor=0x174f, product=0xa311) at libusb:005:004
found USB scanner (vendor=0x04a5 [Color], product=0x20b0 [ FlatbedScanner 23]) at libusb:002:037

and i type: scanimage -L   it shows
device `snapscan:libusb:002:037' is a Acer FlatbedScanner23 flatbed scanner

sometimes it changes FlatbedScanner 23 to  "FlatbedScanner 22" ..(when i connect my scanner to computer it shows "22" but it changes when i command scanimage -L or afer my first  scan)

And i edit /etc/sane.d/snapscan.conf to the right firmware

And there is a problem that i just can scan one time and when i scan at second time, the computer tell me there is an I/O Error and then my scanner doesn't work, so that i just can restart my scanner

Any one can help me...

---

