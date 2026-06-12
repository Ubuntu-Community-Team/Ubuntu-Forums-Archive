---
title: "TP-LINK PCI-E WLAN (TL-WN781ND) in 11.10"
date: 2011-12-13
forum: Hardware
---

### Post by tpheiska on 2011-12-13
I recently did a complete system overhaul to my HTPC, upgrading to SSD main drive, external graphics card, and most importantly, installing Mythbuntu 11.10. 

I've had loads of issues most of which I've managed to solve but one critical problem remains. My D-Link USB WLAN adapter used to work flawlessly in the previous setup (with ndiswrapper). Now the connection is intermittent with cmd 12 errors in dmesg. More frustratingly the system freezes completely if I use Transmission or Vuze to download torrents. I suspect these have to do with something that has changed in the kernel and I'm thinking of getting new hardware for wireless. 

I found [http://www.tp-link.com/en/products/details/?model=TL-WN781ND]("http://www.tp-link.com/en/products/details/?model=TL-WN781ND") that seems to work nicely with Ubuntu, at least in the previous versions. Does anyone have an experience with the new ubuntu/kernel version, is this hardware compatible?

---

### Post by Bucky Ball on 2011-12-13
Have you been online via a cable and gotten updates? Then plug in the USB wireless dongle and check System>Administration>Additional Drivers. Anything there for the wireless?

---

### Post by tpheiska on 2011-12-13
> **Bucky Ball said:**
> Have you been online via a cable and gotten updates? Then plug in the USB wireless dongle and check System>Administration>Additional Drivers. Anything there for the wireless?

I was wrong with the dongle type, it was actually an A-Link WNU, more details on trying to get it to work originally can be found here: [A-LINK WNU wireless usb stick doesnt work]("http://ubuntuforums.org/showthread.php?t=1312949").

I can download updates through the wireless also, I think my additional drivers section only shows my graphics card drivers but I'll have to check this.

---

### Post by tpheiska on 2011-12-21
Solved, the aforementioned Network card works like a charm with the 3.0 kernel.

---

