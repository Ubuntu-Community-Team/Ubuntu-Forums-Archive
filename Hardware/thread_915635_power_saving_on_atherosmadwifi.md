---
title: "power saving on atheros/madwifi?"
date: 2008-09-10
forum: Hardware
---

### Post by mma8x on 2008-09-10
i haven't found anything encouraging about this so far, but does anyone know of any power saving features that can be enabled for atheros chipset using madwifi?
lspci:
```
01:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
```

it's responsible for ~30 wakeups in powertop.  i'm able to set txpower, but that doesn't seem to make a difference.  any ideas?

---

