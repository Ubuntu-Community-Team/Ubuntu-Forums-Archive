---
title: "Is there a way too..."
date: 2009-04-18
forum: Installation &amp; Upgrades
---

### Post by mc6415 on 2009-04-18
Right well I have ubuntu running quite nicely on my laptop currently and have it running under wubi on my desktop, my laptop is running the RC of 9.0.4, and my desktop 8.10 now I was wondering is there a way to create an installation media from my laptop for use on my desktop as I would like to move off of wubi and onto a proper ubuntu install, however I don't have a disc to hand, now I know I could download the iso on my laptop or desktop and use that too create a USB startup disk however I would like to do it without downloading the iso just to save a bit of time.

Thanks,
mc6415

---

### Post by lemming465 on 2009-04-19
It's possible to use one system as a package source for upgrading another, but you basically have to set up a more or less complete debian mirror server infrastructure to do it.  So it's probably both easier and faster to upgrade.  If you have good internet connectivity you can do on-line upgrades from 8.10 ("intrepid ibex") to 9.04 ("jaunty jackalope") by *sudo update-manager -d*.  In an offline scenario you'd need to use register a copy of the "alternate install" CD using *sudo apt-cdrom add*.  The live desktop CD's can only be used for new installations, not for upgrades.

---

