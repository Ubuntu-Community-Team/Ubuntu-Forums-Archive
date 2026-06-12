---
title: "Kworld UB445-U"
date: 2013-11-30
forum: Hardware
---

### Post by bigwolf227 on 2013-11-30
Has anyone had any luck getting this USB TV stickto work under linux? I have been trying to get this [insert explative here] thing to work with 0 results. Through my extensive google searches, I have learned a few things. 
This USB TV card uses the cx231xx driver. I downloaded kernel 3.12.1, which has the code for this device, and compiled it. For some unknown reason, when the USB stick is plugged into my computer, the drivers don't get loaded. I made sure that the drivers were selected when I used the menuconfig.

The dmesg command reveals the following:
[ 1455.773909] usb 1-1: new high-speed USB device number 4 using ehci-pci
[ 1455.909808] usb 1-1: New USB device found, idVendor=1b80, idProduct=e43f
[ 1455.909816] usb 1-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 1455.909821] usb 1-1: Product: Polaris AV Capture
[ 1455.909825] usb 1-1: Manufacturer: Conexant Corporation
[ 1455.909829] usb 1-1: SerialNumber: 0000000000

What I would really like to know is, why these drivers aren't getting loaded when I plug this USB stick in?
Also, is there something that I'm not installing / loading?

---

### Post by hendersonjeff on 2014-05-10
[http://linuxtv.org/wiki/index.php/KWorld_UB445-U2_ATSC_Hybrid_TV_Stick](http://linuxtv.org/wiki/index.php/KWorld_UB445-U2_ATSC_Hybrid_TV_Stick)

---

