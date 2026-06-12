---
title: "Video Driver Problems"
date: 2006-04-17
forum: Hardware &amp; Laptops
---

### Post by kashirat on 2006-04-17
Hey all,

I'm trying to install Ubuntu 5.10, on a machine with the following specs:

1GB RAM
DFI LanParty Ultra-D
Opteron 146
EVGA 7800GT

Ubuntu starts up all the way to the login screen.  I can log in.  However, when X starts up, all i get is a scribbly mess in the middle of the screen.  The mouse is NOT frozen up, and I see the brown background of what is (presumably) the background of X.

The entry in x11.conf is 'nv'.

Not sure what else I could be missing..

Thanks!

'k

---

### Post by cilynx on 2006-04-17
Maybe try the binary drivers?

[https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia]("https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia")

---

### Post by kashirat on 2006-04-17
Looks like changing the driver in x11.conf from "nv" to "nvidia" worked.

Sounds like this is using the proprietary nvidia driver instead of the open source driver?

I assume that means the open source driver doesn't support the 7800GT line yet?

---

### Post by cilynx on 2006-04-17
Yup, switching that sets you up with the proprietary driver.  Personally, I don't know how far up the line 'nv' supports these days.  I've been using the prop drivers for quite a while.

---

