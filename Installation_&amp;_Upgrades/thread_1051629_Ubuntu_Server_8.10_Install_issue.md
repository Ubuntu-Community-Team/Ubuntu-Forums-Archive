---
title: "Ubuntu Server 8.10 Install issue"
date: 2009-01-26
forum: Installation &amp; Upgrades
---

### Post by ghettofreeryder on 2009-01-26
Hi Guys.  Ive been scratching my head with this one for a few days now.  First off, here is my hardware

Gigabyte MA78G-DS3H motherboard
AMD 5000+ processor
4 GB ram
Intel PT Quad port nic
Adaptec 31605 Raid card.

Anyways, here is the issue.  The actual installation goes smooth however, it doesnt boot.  It doesnt matter if the drive is set for AHCI, raid of IDE, nothing at all.  WIth raid, it drops to busybox and says something about /dev/mapper/xxx is missing.  I tried roodelay=900, didnt help.  With AHCI, when installing it, after detecting the HD, it says Serial ATA raid data found, do you want to enable.  If I say yes, the installer finds no drives.  If I say no, it find the drives, but never boots after the install.  Can someone give me a hand?

This is with the raid card removed, using the onboard ports.  Also, this is using Ubuntu server x86_84

---

