---
title: "Epson CX4000 Scanner doesn't want to work"
date: 2006-11-30
forum: Hardware &amp; Laptops
---

### Post by DoctorMO on 2006-11-30
I have a CX4000 scanner/printer, I bought it because it's a supported device; and the printer works perfectly.

unfortunately the tales that the scanner part worked perfectly are less than truthful.

I have seen posts of people who have got this device to work with ubuntu 6.10 just by typing in scanimage -L but this is not the case here.

what I have tried:

recompiling sane 1.0.18
giving everyone access to the usb node
looking at the dmsg logs for errors

scanimage -L with or without sudo produces no results.

Any help would be greatly appreciated.

---

### Post by gjtoth on 2006-11-30
A workaround until I can come up with something better:  Try gksu scanimage   or    gksu xsane   

You'll get a warning but it works for me on my RX620

---

### Post by DoctorMO on 2006-11-30
Ah your problem is a node problem, you need to change your udev rules for that device so it's permissions are changed to 660 root:scanner, you can do this for one time (reset at boot) by doing the following:

find your device in the lsusb list and change that udev node with chmod/chown

modifying the udev rules in etc is the best option though because it's not reset.

My problem it appears was that this device only works with epsons own Linux sane driver that everyone forgot to mention is required for most epson scanners to work.

---

