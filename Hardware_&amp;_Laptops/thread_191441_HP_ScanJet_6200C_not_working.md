---
title: "HP ScanJet 6200C not working"
date: 2006-06-07
forum: Hardware &amp; Laptops
---

### Post by uburoi on 2006-06-07
Hi, I have problems with HP Scanjet 6200C: XSane recognizes it, but when I try to do a "preview" or a definitive scan, nothing happens, and the scanner + xsane freeze.  I checked on the SANE site and ScanJet 6200C is on the list of fully supported scanners.
In short: xsane does recognize the scanner, but cannot handle it.
Any idea ?  
TIA, cheers

---

### Post by ola on 2006-06-07
I couldn't get my HP Scanjet 5370C working with XSane so I have to use a program called VueScan ([http://www.hamrick.com/](http://www.hamrick.com/)) it's not free but at least I could get my scans done, so that might be an alternative.

---

### Post by grendel_khan on 2006-06-18
I just had a similar problem; sane-find-scanner would see it, but xscanimage -L wouldn't. Inexplicably, restarting gimp and power-cycling the scanner made it work. I'd complain extensively about the likely sketchiness of my 6200C, but it was used and cheap, and the results are just as good as I need.

---

