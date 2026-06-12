---
title: "Warning while updating 8.04LTS to 8.10"
date: 2009-09-19
forum: Installation &amp; Upgrades
---

### Post by kakila on 2009-09-19
Hi All, 
I got this message while doing the update
-------------

Could not install '/var/cache/apt/archives/ubuntustudio-menu_0.11_all.deb'

The upgrade will continue but the '/var/cache/apt/archives/ubuntustudio-menu_0.11_all.deb' package may be in a not working state. Please consider submitting a bugreport about it.

there is no script in the new version of the package - giving up

-------------

so? Shall I worry about this before doing the next update to 9.04?

---

### Post by Partyboi2 on 2009-09-20
Hi, it means that package was not installed, if you managed to finish the upgrade to 8.10 open a terminal and try installing that package
```
sudo apt-get update && sudo apt-get install ubuntustudio-menu
```

---

