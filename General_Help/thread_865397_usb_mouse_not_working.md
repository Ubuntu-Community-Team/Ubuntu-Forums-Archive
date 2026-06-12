---
title: "usb mouse not working"
date: 2008-07-20
forum: General Help
---

### Post by Cruz on 2008-07-20
Hello,

I just installed Ubuntu 8.04 amd64 and my usb mouse is not recognized. It didn't work during the installation either. After I first booted from the installation CD to see if it works I had two mice connected, the usb one plus a PS/2 mouse. The PS/2 mouse worked, but I unconnected it, because I want to use the usb mouse only. Then I rebooted and started the installation right away hoping it will see the usb mouse during the installation, but it never did. Here is the output of lsusb

Bus 005 Device 004: ID 0e8f:0003  
Bus 005 Device 003: ID 05e3:0605 Genesys Logic, Inc. USB 2.0 Hub [ednet]
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 1532:0101  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

Obviously it doesn't see the mouse, but it recognized a USB hub I have connected, so it can't be all bad. What can I do about the mouse?

Thanks
Cruz

---

### Post by coffeecat on 2008-07-20
Most likely you need to go into the BIOS and change a setting there. USB mice will certainly work with Ubuntu. Do you know how to get into your system's BIOS?

**Edit:** Sorry, I didn't make myself clear. In three systems I have built, the BIOS in the motherboard in each case had USB mouse disabled in the default settings. I had to enable it in the BIOS before a USB mouse could be detected by the OS.

---

### Post by Cruz on 2008-07-20
Nope, there is nothing in the BIOS. I can only enable/disable the USB controller as a whole. However, I switched two USB plugs and now the mouse is working. Whatever.

Thanks
Cruz

---

