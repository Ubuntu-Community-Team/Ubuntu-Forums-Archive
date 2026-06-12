---
title: "clean install no cd"
date: 2009-04-23
forum: Installation &amp; Upgrades
---

### Post by davebridges on 2009-04-23
I normally do a clean install rather than an upgrade, but somewhere around 8.10 ish my cd drive stopped working (i think it was a baby stuffing things inside issue, not a software issue).  What is the best way to do a clean install with a wonky cd drive

---

### Post by Synthros on 2009-04-23
This might help:

[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

About halfway down the page, there is a section dedicated to installing Ubuntu without a CD.

---

### Post by davebridges on 2009-04-24
I have a more serious problem now.  I tried booting from an install partition as per the above link and it crashed during the re-partitioning.  Now i get a grub error 22 when i try to startup and can get no further.  Please tell me my laptop is not bricked now

---

### Post by bladeswords on 2009-04-24
have you considered doing a PXE boot?  Do you have another computer that you could use to help out with the install?

---

### Post by meeples on 2009-04-24
booting from a usb flash drive would be the easiest way i would think :)

---

### Post by meeples on 2009-04-24
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)  :D

---

### Post by davebridges on 2009-04-24
unfortunately the usb drives havent been working in a while either.

---

### Post by bladeswords on 2009-04-24
I had the same problem and I recently got Jaunty installed using only the network.  So if you have another computer that you can use you have a good chance that you can do your install over the network.

[http://hugi.to/blog/archive/2006/12/23/ubuntu-pxe-install-via-windows]("http://hugi.to/blog/archive/2006/12/23/ubuntu-pxe-install-via-windows")  This is the guide that I used.

---

### Post by davebridges on 2009-04-25
i actually ended up swapping in a functional cd drive, and that worked fantastic.  thanks for the suggestions

---

