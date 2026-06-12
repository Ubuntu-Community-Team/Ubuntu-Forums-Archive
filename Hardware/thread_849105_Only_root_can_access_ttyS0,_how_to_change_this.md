---
title: "Only root can access ttyS0, how to change this?"
date: 2008-07-04
forum: Hardware
---

### Post by svennils on 2008-07-04
Hi, 
Im running Gutsy 7.10 on a compaq nc8000 and on reinstalling vmware on this laptop i cannot access the serial port. I tried with minicom, as root all is well, as user i get the error message "minicom: cannot open /dev/ttyS0: No such device".
Tried to set write permissions 666 on /dev/ttys0 since user can see but not access the device, but no change. Vmware gives the same error, even when i run it as root with gksudo. I need the serial port for programming a device through windoze, and for some strange reason i don't want it directly on my hard drive. Any ideas?

---

