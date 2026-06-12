---
title: "RAID issues"
date: 2009-07-01
forum: Installation &amp; Upgrades
---

### Post by jaredheath on 2009-07-01
Bah nvm

Sudo was the entire issue

---

### Post by jaredheath on 2009-07-01
I found an old post referring to using fdisk to do this but fdisk seems to not want to find ANY of my disks...including /dev/sda which is mounted and running.

I am quite certain I'm missing something obvious with this step.  One thing I'm seeing in /etc/fstab is alot of UUID entries rather than actual device names...is this why fdisk isn't seeing anything?

---

