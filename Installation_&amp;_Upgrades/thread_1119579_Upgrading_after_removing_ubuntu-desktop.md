---
title: "Upgrading after removing ubuntu-desktop?"
date: 2009-04-08
forum: Installation &amp; Upgrades
---

### Post by Big_Croc7 on 2009-04-08
If I remove the ubuntu-desktop package, what kind of problems will it cause on doing a dist-upgrade?  The description says "It is also used to help ensure proper upgrades, so it is recommended that it not be removed."  If I remove a package that ubuntu-desktop depends on what happens when I try the upgrade?

---

### Post by ddrichardson on 2009-04-08
They don't mean dist upgrade, the reason meta packages are used is to group packages that work well together but don't need each other to work. Having this package means you have all the elements of a standard Ubuntu desktop - you can still dist upgrade without it.

---

