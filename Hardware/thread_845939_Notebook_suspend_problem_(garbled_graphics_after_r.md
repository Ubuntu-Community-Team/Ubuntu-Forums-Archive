---
title: "Notebook suspend problem (garbled graphics after resume)"
date: 2008-07-01
forum: Hardware
---

### Post by blueturtl on 2008-07-01
On my wife's Compaq nx6125 notebook, suspend works fine even with the fglrx driver. There is a strange caveat to this though:

We have a wireless USB dongle (ZyDAS WLA-54L WiFi) that is supported by Ubuntu. If the wireless card is not plugged in when suspending, the graphics will be horribly garbled on resume. Logging out and logging back in will fix this.

If the wireless card is attached, all will go well with the exception that the wireless dongle will not power off during suspend and I get 0-3 of these error messages right before the machine suspends:
```
[76350.302417] zd1211rw 8-6:1.0: error ioread32(CR_REG1): -22
```

I'm out of my depth here; why does the wireless dongle's existence affect the graphics, and why does it not enter power save mode with the notebook?

---

