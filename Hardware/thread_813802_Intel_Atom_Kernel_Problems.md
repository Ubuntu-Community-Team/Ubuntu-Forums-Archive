---
title: "Intel Atom Kernel Problems"
date: 2008-05-31
forum: Hardware
---

### Post by neilneil2000 on 2008-05-31
I have just bought one of these lovely Intel Atom boards:

[http://www.tranquilpc-shop.co.uk/acatalog/Motherboards.html](http://www.tranquilpc-shop.co.uk/acatalog/Motherboards.html)

which has replaced the Athlon XP I was running initially.

I now have everything up and running with kernel 2.6.22-14-generic

However attempting to load

2.6.22-16-generic or
2.6.22-17-generic

causes the boot process to fail at modprobe.

Does anyone have any ideas why this is happening?

---

### Post by neilneil2000 on 2008-06-24
UPDATE:
2.6.24-19-generic solves boot issues.

The problem was the Ethernet driver.

I have not yet confirmed whether or not the Ethernet port is working however

---

