---
title: "Have USB expansion, need to know if it's 2.0 or 1.1"
date: 2009-10-29
forum: Hardware
---

### Post by dodle on 2009-10-29
I have a USB expansion card/unit.  Is there any way to know which USB version it is.  It is not a PCI card.  It does fit in the expansion slots at the back of the computer where a PCI card would normally go, but it connects to the on-board 9-pin USB.  There is no information, on the unit, about manufacturer or anything.

**Edit:** Actually, now that I think about, since it connects to the motherboard, it is the motherboard that determines the version, isn't it?  The reason I am asking this is because the rear USB connectors on my mom's computer are 1.1.  But I want to upgrade her to 2.0 for her webcam's sake.  So, my guess is that I will have to get a PCI expansion card that is USB 2.0.  Am I correct?

---

### Post by jasonab on 2009-10-30
Open terminal and run lsusb
or for verbose information you can try
lsusb -v | more

Another favorite lspci -v | grep -i usb

---

