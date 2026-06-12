---
title: "Small wireless problem with feisty ndiswrapper and 4318"
date: 2007-04-20
forum: Hardware &amp; Laptops
---

### Post by feed_sparky on 2007-04-20
My broadcom 4318 card works perfectly with feisty using ndiswrapper, but the only way I can get it to work is by turning it off and then back on right after startup (I have a button above my media keys to do this). Otherwise the little icon in the taskbar just spins until it times out. When I turn off/on it starts and connects right away.... It worked just fine in edgy...

I am using ndiswrapper 1.9 and bcmwl5.inf on a HP dv5215us laptop. I had tried using bcm43xx but it just didn't work right, sometimes it would just stop working or work really really slow, with ndiswrapper I always have a strong connection, it's just annoying to have to turn my wireless off then on to get it to work.  I did blacklist bcm43xx.

Any ideas?

---

### Post by Kobalt on 2007-04-20
You must be missing the **auto wlan0** (or whatever flag your wireless interface is) line in your */etc/network/interfaces* file ...

---

### Post by feed_sparky on 2007-04-20
> **Kobalt said:**
> You must be missing the **auto wlan0** (or whatever flag your wireless interface is) line in your */etc/network/interfaces* file ...

Actually it's there 

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

```

---

