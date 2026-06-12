---
title: "DWA-642 on Ubuntu 8.10"
date: 2009-02-20
forum: Hardware
---

### Post by itsluy on 2009-02-20
I have an old P3 laptop (sager 2200t...don't ask) and am trying to use the dwa-642.
The wireless card "works", as it was able to connect to my network (without any special input from me on a fresh install).

I noticed that the wireless is extremely slow. I'm not talking 56k slow, I'm talking cannot even measure the speed effectively slow...

So I'm looking deeper into this issue and I see that i have 2 wireless configurations, one is called wlan0 (which is connected) and then another called wmaster0 which says Unknown Interface

An lshw command shows wmaster0 as the only wireless interface and says it's using an ath9k driver, there is no listing for wlan0 (which is the one that actually "works")

I'm fairly new to ubuntu, and am starting to upgrade to wireless N so I'd really like this thing to work.

---

### Post by itsluy on 2009-02-23
bump...

---

