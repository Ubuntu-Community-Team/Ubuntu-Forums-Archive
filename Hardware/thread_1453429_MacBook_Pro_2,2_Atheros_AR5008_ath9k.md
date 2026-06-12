---
title: "MacBook Pro 2,2 Atheros AR5008 ath9k"
date: 2010-04-13
forum: Hardware
---

### Post by jonnjonzzn on 2010-04-13
Does anyone having a working, reliable solution for this wireless chipset on Lucid?  I have tried out of the box with all updates, with backports-modules-wireless and the stable linux wireless releases.  My hardware is in Title line.  Any help appreciated.  I am _still_ experiencing the dreaded disconnect/reconnect that has been around forever...

---

### Post by ultiva on 2010-04-13
My Sony Vaio with AR9285 hates ath9k driver, but works OK with madwifi:

svn co [http://madwifi-project.org/svn/madwifi/trunk/](http://madwifi-project.org/svn/madwifi/trunk/) madwifi_last

This module (ath_pci) compiles smoothly on karmic and lucid, just need to install build-essential. Don't forget to blacklist ath9k and ath5k after installing this driver. My chip needed additional patches I've found on madwifi-project.org - support for 9285 ported from freebsd.

---

### Post by eugene19 on 2010-05-19
I've tried all sorts of drivers and also wicd, but have no success with the atheros chip in the macbook...

Hope somebody will find a good solution.

---

### Post by davavanstone on 2010-05-22
Im interested in this too, ive got the ar5008 in my toshiba p300, been trying to set it up for months to get n speeds working and some sort of stability but no luck...

---

