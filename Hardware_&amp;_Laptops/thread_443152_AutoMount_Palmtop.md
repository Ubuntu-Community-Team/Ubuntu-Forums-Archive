---
title: "AutoMount Palmtop"
date: 2007-05-14
forum: Hardware &amp; Laptops
---

### Post by obduk on 2007-05-14
I have a psion palmtop and have managed to find a program to mount it which works fine. I was wandering how to do this automatically, knowledge of the specific program is probably not needed.

To mount it manually first I run
ncpd
which listens to the serial port for when the device connects / dissconects, I assume I want to start this process at startup.

Secondly I run
plpnfsd -d mountpoint -u user
to actually mount the device.

How would I get this to mount automatically when I plug in the device.

Thank you, Owen

---

### Post by Spartan.II.117 on 2007-05-14
The first i can help with, the second not, go to system > Prefrences > Sessions click new then type ncpd and save it.

---

