---
title: "camera not detected"
date: 2006-09-29
forum: Hardware &amp; Laptops
---

### Post by chylee on 2006-09-29
I just got a sony quickshot camera and would like to download the picture onto my computer. The problem is when I plug the camera into kubuntu camera doesn't register, no icon appears for me to download the photo's. I have done a few checks to see if kubuntu is picking up any information form the camera.

I tried 'lsusb'  and it does detect the card.

Bus 006 Device 017: ID 054c:0010 Sony Corp. DSC-S30/S70/S75/F505V/F505/FD92 Cybershot/Mavica Digital Camera

I have also tried 'dmesg |grep usb' and I get this

[17183087.504000] usb 6-3: new high speed USB device using ehci_hcd and address 17

The camera has no problems in windows which is on the same computer, and works on debian

---

### Post by mgmiller on 2006-10-02
Have you tried different USB ports?  Some ports on the case can have different power levels on them, although power shouldn't be an issue with this kind of transfer.  You can also try getting an inexpensive USB card reader and put the memory card from the camera in that.  Try running an Ubuntu live CD to see if the camera is correctly recognized by gnome.  Maybe this is a KDE issue.

---

