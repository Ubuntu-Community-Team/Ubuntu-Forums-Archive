---
title: "Sudden, random dependencies on &quot;splix&quot; after upgrade to Jaunty"
date: 2009-05-07
forum: Installation &amp; Upgrades
---

### Post by Fatman_UK on 2009-05-07
Hi all.

I just upgraded two systems from Intrepid to Jaunty. Both of them installed the package "splix" which as far as I can tell is a Samsung printer driver. I have no Samsung devices.

$ sudo aptitude purge splix

warns me:

The following packages will be REMOVED:
  jfsutils{u} libevent1{u} libntfs10{u} libqt3-mt{u} ntfsprogs{u} privoxy{u} socat{u} splix{p} tsocks{u} xfsprogs{u} 

Hmm, I need a lot of those packages. Better keep splix for now.

I'm confused - why do these packages suddenly depend on splix? Could my package databases (on two systems) have been corrupted by the upgrade?

TiA.

---

