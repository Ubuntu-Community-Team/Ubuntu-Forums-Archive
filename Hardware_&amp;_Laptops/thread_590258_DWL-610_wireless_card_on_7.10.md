---
title: "DWL-610 wireless card on 7.10"
date: 2007-10-24
forum: Hardware &amp; Laptops
---

### Post by yangchengkai on 2007-10-24
Hi, guys

I met a strange problem with my DWL-610 wireless card on 7.10. Every time i plug the card into the pcmicia slot, it looks like working fine; but when it connects to a network, the 7.10 will crash, the screen is locked and just the CAPS LOCK is flashing...then i have to restart sys manually.

Anybody has the same problem with me? Anyone fixed it?

Thank you very much...

---

### Post by kismi on 2007-10-26
i have the same problem. but only with activated WEP of my router D-LINK 514.without WEP it's working fine.

---

### Post by Alphajet on 2007-10-29
Hello,

I have exactly the same problem :
- the card works with the windows driver thanks to ndiswrapper
but it only works without a WEP key. Anyway, the network seemed to be slow.

On a WEP protected network, it's impossible to connect. Once the configuration has changed, caps lock is flashing and there's a big freeze.

It seems there is an issue somewhere. Where can we post that bug ?

---

### Post by Vitello on 2007-12-15
I have the same problem since Feisty, anyone has a solution? 

Vitello

---

### Post by Mr.Auer on 2007-12-23
I have the EXACT same bug. Card DWL-610 worked just fine until I entered my WEP key for the first time. Now it causes a kernel panic every time I attach the card or if its attached when booting up. Most annoying.

If anyone knows of a fix or what package is causing this (or is it a kernel driver bug?) we could at least file a bug report.

According to another post, there were some probs with dwl-610 on Hardy kernel as well.

---

