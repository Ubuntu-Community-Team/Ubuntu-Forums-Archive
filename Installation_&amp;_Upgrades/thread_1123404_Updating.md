---
title: "Updating"
date: 2009-04-12
forum: Installation &amp; Upgrades
---

### Post by squirrelfu on 2009-04-12
I have two Ubuntu 8.04 installations, one desktop PC and a laptop PC.

My desktop has just finished downloading and installing updates (all 350 megs of it). Now my laptop wants to update. Bandwidth is terribly expensive where I live, so every last meg counts, :lolflag:! So is there a way to update my laptop with the files already downloaded by my desktop?

Thanks in advance.

---

### Post by Linteg on 2009-04-12
Yes there is, downloaded packages are usually stored in /var/cache/apt/packages/. So if possible, copy the files in this folder from the desktop to the laptop.

---

### Post by squirrelfu on 2009-04-12
> **Linteg said:**
> Yes there is, downloaded packages are usually stored in /var/apt/cache/packages/. So if possible, copy the files in this folder from the desktop to the laptop.

Thanks, that worked a treat! Copied the files and fired up the update manager, only needed to install 20 megs updates specific to that pc.

But for future reference, its located at /var/cache/apt in 8.04

Thanks again. ):P

---

