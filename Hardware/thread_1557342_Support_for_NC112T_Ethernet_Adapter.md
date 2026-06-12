---
title: "Support for NC112T Ethernet Adapter"
date: 2010-08-20
forum: Hardware
---

### Post by pollito_ko on 2010-08-20
Hi everyone!, 

Can anyone tell me if there are a way to install the NIC NC112T Gigabit Server Adapter. 
At HP webpage (indeed) there are no support for Ubuntu plataform...:-k why it does not surprise me?

Thanks in advance for all your help!. PoLKo

---

### Post by pollito_ko on 2010-08-20
Okay, I found direct Intel driver support, so now I'm in dutch again, I dont know quite what package compiler is requesting!!:

root@svtmx03:/Resources/Drivers/e1000e-1.2.10/src# make check
Makefile:71: *** Kernel header files not in any of the expected locations.
Makefile:72: *** Install the appropriate kernel development package, e.g.
Makefile:73: *** kernel-devel, for building kernel modules and try again.  Stop.
root@svtmx03:/Resources/Drivers/e1000e-1.2.10/src#

Any clue???

Thanks.

---

