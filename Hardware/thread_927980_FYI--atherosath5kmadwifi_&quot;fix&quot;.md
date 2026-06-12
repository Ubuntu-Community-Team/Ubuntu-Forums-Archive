---
title: "FYI--atheros/ath5k/madwifi &quot;fix&quot;"
date: 2008-09-23
forum: Hardware
---

### Post by mma8x on 2008-09-23
ok, not really a fix.  when using the ath5k module (similar probs using the madwifi mods with kernel 2.6.24), occasionally i was unable to find anything with "iwlist wlan0 scan" ("no results").  dmesg gave me 
```
ath5k phy0: unable to reset hardware: -11
```
and/or
```
ADDRCONF(NETDEV_UP): wlan0: link is not ready
```
anyway, after much googling and finding the problem (but of course, not the solution) posted, it turns out that a hard power down is necessary to reset the radio.  just doing a "restart" isn't enough, the computer must be physically off.  hopefully this saves someone some time...

---

