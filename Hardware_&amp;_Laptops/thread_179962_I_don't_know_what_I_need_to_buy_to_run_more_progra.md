---
title: "I don't know what I need to buy to run more programs at once"
date: 2006-05-21
forum: Hardware &amp; Laptops
---

### Post by shutupimpoor on 2006-05-21
I want to simutaniously run things like Banshee media player and my n64 emulator at the same time, without the computer lagging a lot. I currently am running:

P4 3.2 Ghz prescott h.t. 800MHz FSB
(2) PC3200 512MB 
GeForce Fx5500 256 MB
Foxconn 865A01-PE Motherboard

(i know some of the details are extra, but I don't know what I need to upgrade)

---

### Post by GarethMB on 2006-05-21
RAM. If you're PC can take it you need more RAM

---

### Post by adamkane on 2006-05-21
You want to install the correct kernel packages to get your system to run multiple apps without performance degradation.

```

sudo apt-get install linux-686 linux-headers-686

``` 
Reboot.

---

### Post by dicecca112 on 2006-05-21
he should be fine ram wise with that pc.  I think adamkane is right with him using the wrong kernel.  Even my dual core lags when I don't have the 686s installed

---

