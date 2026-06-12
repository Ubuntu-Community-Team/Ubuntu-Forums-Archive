---
title: "MA600 serial irda and Breezy"
date: 2005-11-29
forum: Hardware &amp; Laptops
---

### Post by MarioFrick on 2005-11-29
I looked at many discussions about irda issues on this forum, but they didn't help to solve my problem.

I have a MA600 irda serial dongle and Breezy, but I cannot make it work.
If I type lsmod I have:
irda                  188412  3 irtty_sir,sir_dev,via_ircc

I installed ircp, irda-utils and openobex-apps. 

I wrote that too:
```
# Set dongle type, e.g. none, tekram, esi, actisys, actisys+, ep7211, girbil,
# litelink, airport, old_belkin, mcp2120, act200l, ma600). You do not need
# a dongle for FIR mode.
DONGLE="ma600"
```

but any time I type sudo irdadump nothing happens... :(

Any idea? :confused: 

Thanks in advance! :)

---

### Post by nicky75 on 2006-01-19
I have the same problem :confused:

---

