---
title: "HP photosmart 7260 not recognized"
date: 2007-02-10
forum: Hardware &amp; Laptops
---

### Post by eombah on 2007-02-10
Hi,

I plugged my HP photosmart 7260 printer in a USB socket but it isn't recognized by Ubuntu.

Unpluging it and plugging it back in (in a different socket) gives in dmesg:
[17234763.864000] usb 2-2: USB disconnect, address 4
[17234776.636000] usb 1-2: new full speed USB device using uhci_hcd and address 4
[17234776.820000] usb 1-2: configuration #1 chosen from 1 choice

and lsusb then gives:
Bus 005 Device 007: ID 0424:2504 Standard Microsystems Corp. 
Bus 005 Device 006: ID 0424:2502 Standard Microsystems Corp. 
Bus 005 Device 002: ID 059b:0274 Iomega Corp. 
Bus 005 Device 008: ID 0424:223a Standard Microsystems Corp. 8-in-1 Card Reader
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 046d:c501 Logitech, Inc. Cordless Mouse Receiver
Bus 003 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 04b8:011d Seiko Epson Corp. Perfection 1260 Photo
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 045e:000b Microsoft Corp. Natural Keyboard Elite
Bus 002 Device 001: ID 0000:0000  

Any ideas?

regards Bart.

---

