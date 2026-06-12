---
title: "Remove Evolution/Totem"
date: 2005-11-09
forum: General Help
---

### Post by cavaughan on 2005-11-09
I want to remove Evolution and Totem, but when I try to do so - whether through Synaptic, dpkg, dselect - it says I have to remove ubuntu-desktop. How can I remove these packages? I don't use them, I don't need them.

---

### Post by Kapre on 2005-11-09
[QUOTE=cavaughan]I want to remove Evolution and Totem, but when I try to do so - whether through Synaptic, dpkg, dselect - it says I have to remove ubuntu-desktop. How can I remove these packages? I don't use them, I don't need them.[/QUOTE]

cavaughan - You can remove the ubuntu desktop (if you want to remove Totem and Evolution), The Ubuntu desktop is an app itself and would not affect the system if removed.

K

---

### Post by RAOF on 2005-11-10
Specifically, the "ubuntu-desktop" package is a "metapackage" - it exists only to depend upon other packages, but doesn't actually contain anything itself.  So, ubuntu-desktop depends upon all of the programs you find in a clean install of Ubuntu.  It is totally safe to remove (it doesn't actually contain any programs itself).

If and when you want to update your Breezy install to the next Ubuntu version (Dapper), you should install ubuntu-desktop again first - that way, all the new programs in Dapper will be installed.

Be careful when removing Evolution.  Specifically, evolution-data-server is used by much of Gnome, the desktop environment, so don't remove that.

---

