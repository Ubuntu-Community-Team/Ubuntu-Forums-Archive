---
title: "Minimal install + UTC"
date: 2009-07-30
forum: Installation &amp; Upgrades
---

### Post by Xyem on 2009-07-30
So I believe I may have found a bug in the minimal install, just wondering if others had come across it and might be able to direct me to the "proper" way of doing it or a fix I can do during installation. Also, if someone could direct me to the source for the minimal install, maybe I can see what it is doing ( and patch it.. )

Basically, my hardware clock ( BIOS ) is set to UTC. My current timezone is BST ( UTC+1 ) and during the installation, Ubuntu asks if the system clock is UTC. Regardless of whether I answer yes or no, the installer changes my hardware clock an hour forward. Surely, answering "yes" means that I don't want the system clock changing?

This happens on the 8.10 minimal installer and the 9.04 installer.

---

### Post by Xyem on 2009-07-30
I think I've found the problem but I have found a workaround.

Logged a bug on launchpad against clock-setup: [https://bugs.launchpad.net/ubuntu/+source/clock-setup/+bug/407137](https://bugs.launchpad.net/ubuntu/+source/clock-setup/+bug/407137)

---

