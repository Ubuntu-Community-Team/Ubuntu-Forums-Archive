---
title: "Atheros card mysteriously disappeared?"
date: 2008-11-02
forum: Hardware
---

### Post by BoyBlunder on 2008-11-02
I just installed 8.10 on my Acer Aspire One, and had wireless up and running after running the command: ```
aptitude install linux-backports-modules-intrepid-generic
```

I was up and running until I did some more tweaks (nothing network related, stuff related to trackpad, etc) and I noticed that my wireless cut out. I checked the hardware drivers and noticed that my ath5k driver was gone, and nothing was listed.

how do I resolve this? I've tried reinstalling the backports-modules but it hasn't resolved anything. lspci | grep net only shows my ethernet card; no wireless.

please help!

---

### Post by BoyBlunder on 2008-11-02
anyone?

---

### Post by webdevmydnac on 2008-11-02
Ive got same problem. That and madwifi being down doesnt help

---

### Post by Jesterday on 2009-01-21
I have the same issue, I was transferring files over the network yesterday and all of a sudden I got disconnected and it no longer showed the existence of a wireless card. It was weird. Same system, an Acer Aspire One.

hhhmmm...gonna have to check out the whole madwifi thing again.

---

### Post by RJARRRPCGP on 2009-01-21
Sounds like a connector has bad contact. Like when a USB device isn't plugged in all the way.

---

