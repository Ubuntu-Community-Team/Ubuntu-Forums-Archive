---
title: "inateck 4 port pci-e USB3 card suddenly stops reading"
date: 2019-05-23
forum: Hardware
---

### Post by atombear on 2019-05-23
A few days ago we installed [https://www.inateck.com/inateck-ktu3fr-4p-usb-3-0-pci-express-karte-mit-4-usb-3-0-ports.html](https://www.inateck.com/inateck-ktu3fr-4p-usb-3-0-pci-express-karte-mit-4-usb-3-0-ports.html) into a dell poweredge 730, and after activating USB3 in the bios, it seemed to work fine. In the interim, we updated packages on the machine, and after a restart or two, the computer no longer recognizes usb devices. plugging a keyboard in, the keyboard lights do not activate. I am not sure what could have changed. This is from the upgrade logs:

2019-05-13 15:12:58 install libusb-0.1-4:amd64 <none> 2:0.1.12-31
2019-05-16 06:31:33 install linux-modules-4.18.0-20-generic:amd64 <none> 4.18.0-20.21~18.04.1
2019-05-16 06:31:36 install linux-image-4.18.0-20-generic:amd64 <none> 4.18.0-20.21~18.04.1
2019-05-16 06:31:37 install linux-modules-extra-4.18.0-20-generic:amd64 <none> 4.18.0-20.21~18.04.1
2019-05-16 06:31:46 install linux-headers-4.18.0-20:all <none> 4.18.0-20.21~18.04.1
2019-05-16 06:32:02 install linux-headers-4.18.0-20-generic:amd64 <none> 4.18.0-20.21~18.04.1
2019-05-18 15:35:45 install input-utils:amd64 <none> 1.0-1.1build1

Any ideas?

---

### Post by rbmorse on 2019-05-23
My personal experience with Inateck hardware hasn't been all that good.  

I'd shut down, pull the card, examine it for signs of overheating/bad solder connections (a good hand magnifier will be useful) or other obvious signs of failure.  

Reinstall the card, make sure it is _fully_ seated in the slot and that it doesn't get pulled out of alignment when you tighten the retaining screw. The spacing between contacts in a PCI slot is very tight...not much room for mis-alignment.  

Make sure there's no physical clearance issues with adjacent cards.  

If you're using the external power connector, make sure that's fully inserted into the socket (both ends).  

If it still doesn't work, the next thing to do would be to try it in another machine.

---

### Post by atombear on 2019-05-24
Thank you. I should also mention that lspci yields the following entry, which I assume to be the card: 82:00.0 USB controller: Fresco Logic FL1100 USB 3.0 Host Controller (rev 10).

---

### Post by rbmorse on 2019-05-24
What does lsusb say about it?

---

