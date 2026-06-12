---
title: "Ethernet may be broken, refuses to connect to wireless networks"
date: 2010-01-11
forum: Hardware
---

### Post by FreezWay on 2010-01-11
After trying 3 mobos, 2 gfx cards, new RAM, case and power supply, i finally had my computer working, and it did, for 2 weeks, then 2 days ago, Ethernet randomly stopped working, for no reason and I dont have wireless, everything else works great, but i cant go online. I deperatly need to get this fixed (for my sanity.)

Any help would be good.

---

### Post by Saghaulor on 2010-01-11
> **FreezWay said:**
> After trying 3 mobos, 2 gfx cards, new RAM, case and power supply, i finally had my computer working, and it did, for 2 weeks, then 2 days ago, Ethernet randomly stopped working, for no reason and I dont have wireless, everything else works great, but i cant go online. I deperatly need to get this fixed (for my sanity.)

Any help would be good.

Are you plugged directly into your modem, or into a router?

Run ```
sudo ifconfig
``` in terminal. Is your ethernet card showing up? They usually show up as eth0.

---

### Post by FreezWay on 2010-01-11
router, ifconfig tells me shows eth1 as my ethernet device and lo as local loopback.

---

### Post by Saghaulor on 2010-01-11
Have you powercycled the modem and router?

Remember to turn the modem on first, then after it initializes, turn the router back on.

Then you should try the following:

```
sudo ifconfig eth1 down
sudo ifconfig eth1 up
sudo dhclient eth1
```

If all goes well, you should receive an ip address. Then you should be able to connect to the net.

---

### Post by FreezWay on 2010-01-11
worked like a charm, thanks!

---

### Post by Saghaulor on 2010-01-11
> **FreezWay said:**
> worked like a charm, thanks!

No problem, glad that I could help.

---

