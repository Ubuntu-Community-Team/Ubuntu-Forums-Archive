---
title: "Don't work Realtek RTL8111/8168/8411 with 4.15.0-33 kernel"
date: 2018-08-24
forum: Hardware
---

### Post by mikael-box on 2018-08-24
Hi all. Yesterday I got update to my Ubuntu 18.04 with new kernel 4.15.0-33. Now I power up my PC and have been saw what my network card isn't worked. Next I tried to reboot with previous kernel 4.15.0-32 and with it all works fine.
How can I try to fix it?

---

### Post by mattlach on 2018-08-24
Sounds like a regression to me.

I would recommend temporarily just using the previous kernel, and hoping it is fixed in the next update.   

You could also check the known kernel errata, and if there isn't anything there, report it as a bug.

In general, next time you buy hardware, I would avoid anything Realtek.   It's more trouble than it is worth.  Their shirt is always unstable and breaking.    Intel NIC's are much more reliable.   It can be difficult to find a motherboard with Intel NIC's, but it is well worth the effort.

---

