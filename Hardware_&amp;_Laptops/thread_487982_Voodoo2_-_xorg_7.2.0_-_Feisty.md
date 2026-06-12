---
title: "Voodoo2 - xorg 7.2.0 - Feisty"
date: 2007-06-29
forum: Hardware &amp; Laptops
---

### Post by redrum on 2007-06-29
Hello,
I am trying to use an old Voodoo2 with my old computer.
Unfortunately, I did not succeed in using it with xorg.
xorg reject the driver "voodoo" and does not know anymore the driver "glide"
Anybody can help to make me be able to finalize the installation of my old Voodoo2 ?
Regards,

---

### Post by loserboy on 2007-06-29
can you get video after you do 

> sudo dpkg-reconfigure xserver-xorg
note: in case you didnt know this will also reset some settings on your mouse and keyboard

or do you have any video at all right now?

---

### Post by loserboy on 2007-06-29
I found something here but it looks like its directed at voodoo3 users

[https://help.ubuntu.com/community/Voodoo3doesnotdo3d?highlight=%28voodoo%29](https://help.ubuntu.com/community/Voodoo3doesnotdo3d?highlight=%28voodoo%29)

---

### Post by redrum on 2007-06-30
Unfortunately there is a world between voodoo2 and voodoo3 for linux users.
Please find below the Xorg log sample when I try to load driver "voodoo" in Xorg.conf :

> (II) Voodoo: driver for Voodoo1/Voodoo2: Voodoo 1, Voodoo 2
(II) Primary Device is: PCI 01:00:0
(WW) Voodoo: No matching Device section for instance (BusID PCI:0:13:0) found
(EE) No devices detected.

Fatal server error:
no screens found

---

### Post by loserboy on 2007-06-30
well thats crappy, I bet you could find a working card for like 15 bucks though if you live in the US

---

