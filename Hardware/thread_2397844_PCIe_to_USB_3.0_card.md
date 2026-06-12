---
title: "PCIe to USB 3.0 card"
date: 2018-08-04
forum: Hardware
---

### Post by bobsone on 2018-08-04
Hi
 
I have Ubuntu mate 18.04 on a desktop; I have just installed a removable HDD bay which also has 2 female USB 3.0 sockets connected via a 19 pin connector.  Unfortunately the motherboard 19 pin USB 3.0 header is already in use.

  I have been looking at a number of cards, but although they all ‘claim’ to work with windows, there is little to no info on their Mate 18.04 compatibility.  
  Does anyone have experience with PCIe to USB cards, i.e. which ones actually work and will readily work with Ubuntu?
  Thanks.

---

### Post by rbmorse on 2018-08-05
I have an ASUS branded PCIe card that adds one USB 3.1 type "A" and one USB 3.1 type "C" ports. It just works.  

I haven't done any benchmarking to verify the ports are really running at 3.1 speeds, OTOH, there are no error messages and if I plug something into one of the ports on the card the system recognizes it, initializes it and it operates normally. 

edit:  lsusb says this about it:  Bus 006 Device 002: ID 174c:1153 ASMedia Technology Inc. ASM1153 SATA 3Gb/s bridge

The card came with a driver disk but the only thing on it was for old versions of Windows that predate the 3.1 standard.  I forget which Linux kernel added USB 3.1 support, but if your distro is still currently supported you should be OK.

---

### Post by bobsone on 2018-08-10
Thanks for the info rbmorse
I am still looking for a card, I haven't found an Asus card with a 19 pin header.
A bit of info for anyone looking for a PCIe-USB card;
 I have 'acquired' a Silverstone SST-UCU01 (Etron EJ198 chip) expansion card  with 2x19 pin headers, for testing, it works out of the box with windows 8.1 and Mate 18.04 and the speeds look to be about the same as the motherboard 19 pin header, but... 
I have 2 removable drive bays in this desktop (a Enermax EMK5201U3, and a Sharkoon SATA Quick Port), when either of the bays power is switched on the Silverstone card causes the computer to reboot within 3-4 seconds of being shut down but when the drive bay(s) power is switched off, everything works as expected  :confused:

---

### Post by bobsone on 2018-09-08
An update;
I have a cheap solution that works out of the box on windows and Mate 18.04, it is a Rokoo SuperSpeed 2 Port PCIe card from Amazon

[https://www.amazon.de/gp/product/B07CK7ZR6H/ref=oh_aui_detailpage_o00_s00?ie=UTF8&psc=1](https://www.amazon.de/gp/product/B07CK7ZR6H/ref=oh_aui_detailpage_o00_s00?ie=UTF8&psc=1)

---

