---
title: "Installation of packages from USB drive"
date: 2008-12-29
forum: Installation &amp; Upgrades
---

### Post by ANew on 2008-12-29
I was trying to install gparted. If i have live cd 
image iso-file on the flash drive whould will it be possible to
install it without coping file for cd-rom?

I probably need to add direction to this file to repository?

What should i change so "apt-get" will see the package?

---

### Post by mikewhatever on 2008-12-29
You can install gparted from the live cd:

sudo apt-cdrom add <-- Adds the cd to repositories.
sudo apt-get update
sudo apt-get install gparted

---

