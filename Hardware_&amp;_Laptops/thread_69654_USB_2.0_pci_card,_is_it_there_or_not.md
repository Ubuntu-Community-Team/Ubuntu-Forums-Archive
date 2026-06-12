---
title: "USB 2.0 pci card, is it there or not???"
date: 2005-09-27
forum: Hardware &amp; Laptops
---

### Post by Greyfoxwolf on 2005-09-27
just a piece of dmesg
 ```
ehci_hcd 0000:00:09.2: VIA Technologies, Inc. USB 2.0 
ehci_hcd 0000:00:09.2: irq 16, pci mem 0xdf004000 
ehci_hcd 0000:00:09.2: new USB bus registered, assigned bus number 5 
ehci_hcd 0000:00:09.2: USB 2.0 initialized, EHCI 1.00, driver 26 Oct 2004 hub 5-0:1.0: USB hub found hub 5-0:1.0: 4 ports detected 
``` 
does this mean that the usb 2.0 card is installed? im trying to get my external hdd to work but it isnt working (hdd is fine, ext3 format). my external hdd case isnt lighting up, wont work on the usb 1.1 of what im sure that works, even in windows.. i just want to be sure that the usb card is woking (its new and cuz i cant get it working in windows, driver issues, however it does detect a pci device)

---

### Post by Greyfoxwolf on 2005-09-27
well finaly my brain fired up again and i pluged my pocket pc in the usb2 drive. raki doesnt work, but dmesgdoes and it showed the pocket pc, so the pc card is just fine, sory for wasting bytes on the forum

---

