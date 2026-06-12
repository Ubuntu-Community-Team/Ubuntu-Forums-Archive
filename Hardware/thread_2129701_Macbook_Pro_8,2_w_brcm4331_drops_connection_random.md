---
title: "Macbook Pro 8,2 w/ brcm4331 drops connection randomly..."
date: 2013-03-27
forum: Hardware
---

### Post by vardyh on 2013-03-27
I installed Ubuntu 12.10 and extracted Broadcom firmware using b43-fwcutter. That makes my wireless network usable, **BUT** my wireless connection keeps getting **disconnected** periodicly when there's **more than one** machine in my local network. It remains connected as long as there was signal if I'm the only machine in my local network.

Does anybody meets the same issue? Is there any way to get rid of it? If there's not, I have to turn back to MacOSX, which is poorly slow...

PS:

```
lspci --vnn | grep 4331
03:00.0 Network controller [0280]: Broadcom Corporation BCM4331 802.11a/b/g/n [14e4:4331] (rev 02)
```

```
lsmod | grep b43
b43                   369857  0 
mac80211              540032  1 b43
cfg80211              206797  2 b43,mac80211
bcma                   35657  1 b43
ssb                    52037  1 b43

```

---

### Post by vardyh on 2013-03-27
Bump....

---

