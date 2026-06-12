---
title: "cups - Quota limit reached"
date: 2006-04-12
forum: Hardware &amp; Laptops
---

### Post by zigi on 2006-04-12
I don't know why, but I can't print...cups give me an error: Quota limit reached, but I hadn't set up any limits

this I have in my /etc/cups/printers.conf by my default printer:
```

QuotaPeriod 0
PageLimit 0
KLimit 0

```

Q1: How could I solve this problem? Is some way, how reset the limits?

Q2: When my system starts, detects parallel port (/dev/lp0) and loads needed modules (lp, parport_pc), but doesn't detect my printer Lexmark1100 (after login: cat /proc/sys/dev/parport/parport0/autoprobe is empty). If I do this:
```

modprobe -r lp parport_pc
modprobe lp

```
than I can see the printer (cat /proc/sys/dev/parport/parport0/autoprobe)..

Exists better solution than give these two commands into /etc/rc.local ?

PS: I use Dapper Drake 6.06

thx

---

