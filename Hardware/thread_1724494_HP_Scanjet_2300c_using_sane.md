---
title: "HP Scanjet 2300c using sane"
date: 2011-04-08
forum: Hardware
---

### Post by Aurelian60 on 2011-04-08
Hi.

I am trying to use a HP Scanjet 2300c on Ubuntu 10.10 and xsane 0.996. Sane project says device is fully supported and device is detected but both scanimage and xsane fail.

scanimage -V
scanimage (sane-backends) 1.0.20; backend version 1.0.20

scanimage -L
device `genesys:libusb:006:003' is a Hewlett Packard ScanJet 2300c flatbed scanner

scanimage -d genesys:libusb:006:003 --format=pnm > test.pnm
scanimage: sane_start: Error during device I/O

Any ideas? 
Thanks!

---

### Post by Aurelian60 on 2011-04-09
-Update- I tried this drivers   [http://bobthegnome.blogspot.com/2010/11/using-latest-sane-drivers-in-ubuntu.html](http://bobthegnome.blogspot.com/2010/11/using-latest-sane-drivers-in-ubuntu.html)  but both scanimage and xsane fail.

---

### Post by markofealing on 2011-05-16
It would appear that XSANE is broken. My Scanjet 7400c no longer works in 11.04, despite being labelled as compatible.

scanimage -V
scanimage (sane-backends) 1.0.22; backend version 1.0.22

scanimage -L
device `avision:libusb:005:005' is a Hewlett-Packard ScanJet 7400c flatbed scanner.

Scans under the XSANE but produces nothing. Failes to scan using scan2pdf, only works using Simple Scan which I don't believe uses xsane for the back-end, hence it works!

Anyone else?

---

