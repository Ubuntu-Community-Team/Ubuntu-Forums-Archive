---
title: "My Mouse Stops Working HELP PLEASE!!!!"
date: 2007-09-07
forum: Hardware &amp; Laptops
---

### Post by StaticKrunch on 2007-09-07
After awhile my mouse just stops working:mad:. I have tried unplugging and plugging it back up but once it stops working it stops working. In order to get it to work again I have to completely restart my computer, but even then after awhile it stops working again can some one help me?
Below I will give you the results of my lsusb command when my mouse is working and when it stops working, and I will also give you my results of my dmesg command when it stops working

lsusb when mouse is working:
Bus 002 Device 004: ID 413c:3200 Dell Computer Corp. 
Bus 002 Device 002: ID 413c:2003 Dell Computer Corp. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 0644:0200 TEAC Corp. 
Bus 001 Device 001: ID 0000:0000 

lsusb when mouse is not working:
Bus 002 Device 002: ID 0644 : 0200 TEAC Corp.
Bus 002 Device 001: ID 0000 : 0000
Bus 001 Device 007: ID 413c : 3200 Dell Computer Corp.
Bus 001 Device 005: ID 413c : 2003 Dell Computer Corp.
Bus 001 Device 001: ID 0000: 0000

dmesg when mouse is not working:
[    407.716000] usb 1-8: USB disconnect, address 6
[    411.704000] usb 1-8: new low speed usb device using ohci_hcd and address 7
[    411.916000] usb 1-8: configuration #1 chosen from 1 choice
[    411.928000] input: Dell Dell USB Mouse as /class/input/input8

---

### Post by biophysics on 2007-09-07
Do you think there is a hardware loose contact... Try using another mouse.

---

