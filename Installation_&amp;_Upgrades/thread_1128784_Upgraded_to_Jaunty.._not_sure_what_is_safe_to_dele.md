---
title: "Upgraded to Jaunty.. not sure what is safe to delete"
date: 2009-04-18
forum: Installation &amp; Upgrades
---

### Post by azebuski on 2009-04-18
I updated to 9.04 earlier today.  Whenever I update to a new release there are usually hundreds of packages I delete for things I don't need (bluetooth, Korean and Thai fonts, etc.)

Since updating to 9.04, Synaptic is listing some pretty important things (or what I think are pretty important things) in the "obsolete" and "auto removable" categories.

For instance, libdvdcss2, libdvdread3, medibuntu-keyring, slocate, and xfce4-alsa-mixer are listed in the obsolete category.

Gnome-desktop-data, and mbr are listed in the auto removable category among other packages. mbr says it's the master boot record and is used to boot operating systems from the hard drive.

Why are all these things being listed in the obsolete and auto removable sections in Synaptic?

---

### Post by zvacet on 2009-04-18
If you know that you wish these packages then run

```
sudo apt-get update && sudo apt-get upgrade
```

and you will get list of packages for autoremove.Instead of removing them install them again in terminal

```
sudo apt-get install package1 package2
```

---

