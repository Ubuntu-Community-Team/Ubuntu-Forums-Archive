---
title: "HELP! fail safe within 30 sec... and i have no gui now..."
date: 2009-10-26
forum: Installation &amp; Upgrades
---

### Post by gorship on 2009-10-26
Hey, so i installed ubuntu on my comp over vista. I installed all the updates, and the update for my nvidia card... and now when i restart it tells me that it went to failsafe after 30 seconds, because server x is disabled or something...HELP

---

### Post by fancypiper on 2009-10-27
Try running this and see if that will cure it

sudo dpkg-reconfigure -phigh xserver-xorg

---

