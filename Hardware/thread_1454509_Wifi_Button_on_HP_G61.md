---
title: "Wifi Button on HP G61"
date: 2010-04-14
forum: Hardware
---

### Post by craig552 on 2010-04-14
Hello,

I've installed 9.10 in to an HP G61 laptop, and the wifi enable/disable switch is misbehaving.

When I initially turn on the pc, wifi is active, and i can disable it with the keyboard button, but I cannot then re-enable it. To get wireless back i have to restart the pc.

lspci gives the device as:
02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)

The same button simultaneously enables/disables bluetooth without issue.

rfkill shows that the wifi is hardblocked 
But 'rfkill unblock all' cannot unblock it

Any help greatly appreciated.

---

### Post by craig552 on 2010-04-14
Ok, following the instructions at [https://help.ubuntu.com/community/WifiDocs/Device/Atheros/AR9285](https://help.ubuntu.com/community/WifiDocs/Device/Atheros/AR9285) sorted it out...

---

