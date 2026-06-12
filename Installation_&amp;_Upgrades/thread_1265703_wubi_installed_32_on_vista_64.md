---
title: "wubi installed 32 on vista 64"
date: 2009-09-13
forum: Installation &amp; Upgrades
---

### Post by eddyeoq on 2009-09-13
I installed Ubuntu 9.04 using Wubi. I have vista home premium 64 bit, but wubi installed ubuntu 9.04 32 bit instead of 64 bit. system monitor shows two CPUs and says that I have 2.9 Gb when I have 4 gb ram. is there a way to unstall ubuntu 9.04 64bit with wubi? :?:

---

### Post by zvacet on 2009-09-13
I think you have to download Ubuntu desktop CD 64 bit and install with Wubi from there.

---

### Post by raymondh on 2009-09-13
> **eddyeoq said:**
> I installed Ubuntu 9.04 using Wubi. I have vista home premium 64 bit, but wubi installed ubuntu 9.04 32 bit instead of 64 bit. system monitor shows two CPUs and says that I have 2.9 Gb when I have 4 gb ram. is there a way to unstall ubuntu 9.04 64bit with wubi? :?:

You uninstall a WUBI-installed Ubuntu like any windows application.  Use the add/remove option in control panel.  Afterwards, you may want to clean up the boot-ini file.

See this guide

[https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20manually%20uninstall%20Wubi?](https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20manually%20uninstall%20Wubi?)

I am not sure if cleaning the boot.ini is needed since you are going to re-install a 64-bit ubuntu anyways.  I would clean it up (the boot.ini) just so I start with a clean slate.

Back-up your files.  Defrag windows 2x. When done, download the 64-bit and start anew.

Happy ubuntu-ing.

---

