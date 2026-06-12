---
title: "LM Technology Wireless Adapter Not Working"
date: 2013-01-28
forum: Hardware
---

### Post by mattdt on 2013-01-28
My LM Technology 006 wireless adapter with a RealTec chipset won't show up in the Network Manager on my 10.04 LTS system. A USB terminal check shows the device is recognized but won't show in Network Manager. It does work on boot up into Win XP on another HD.

Any ideas?

---

### Post by Yellow Pasque on 2013-01-28
Use a newer kernel (should be a few available in Lucid) and also make sure you have the right firmware installed. It would help to know what chipset the adapter had:
```
lspci
```

---

