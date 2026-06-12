---
title: "HDD in External Enclosure not recognized"
date: 2015-11-16
forum: Hardware
---

### Post by spandey on 2015-11-16
I have Mate desktop in UBUNTU 14.04 LTS. It's a 7 year old PC. I have a put a 750 GB laptop HDD in TRICOM usb 2.0 HDD enclosure. UBUNTU is not recognizing this enclosure. The light just keep blinking. But it is perfectly recognized in Windows laptop. 

I tried lsusb before and after connecting the enclosure in usb port but there is no change. 

Any help will be really appreciated.

---

### Post by Vladlenin5000 on 2015-11-16
The symptom suggests it isn't getting enough power.

---

### Post by spandey on 2015-11-16
I tried connecting to all the 6 usb 2.0 ports but no success. When I connect a Toshiba external HDD in the same USB 2.0 port it works fine. Any clues?

---

### Post by Vladlenin5000 on 2015-11-16
If you have a Y shaped cable (two USB connectors, one for data and power and the other for additional power) try it. Also an externally powered USB hub may work.
Others drives working in the same port isn't as relevant as you might think. Different hardware, different requirements. And from experience I can tell the branded external drives, albeit theoretically being the same*, tend to work better than home assembled enclosures.

* Any external drive you may find are just an internal drive inside an enclosure with an USB-SATA (or PATA) interface adapter. Reliability and overall performance vary a lot though.

---

