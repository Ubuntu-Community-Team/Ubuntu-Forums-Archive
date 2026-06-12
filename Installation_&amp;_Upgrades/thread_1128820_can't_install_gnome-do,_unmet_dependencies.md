---
title: "can't install gnome-do, unmet dependencies"
date: 2009-04-18
forum: Installation &amp; Upgrades
---

### Post by ceverett on 2009-04-18
```
[xander] ceverett@xander:/tmp
14. sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  gnome-do: Depends: libgnomedesktop2.20-cil (>= 2.24.0) but it is not installable
            Depends: libnotify0.4-cil (>= 0.4.0~r2998) but it is not installable
            Depends: librsvg2-2.18-cil (>= 2.24.0) but it is not installable
            Depends: libwnck2.20-cil (>= 2.24.0) but it is not installable
            Recommends: gnome-do-plugins but it is not installed
E: Unmet dependencies. Try using -f.

```
Any clues for me?  I'm on jaunty.  Everything else seems to be working OK, it's just this one thing.

---

### Post by zvacet on 2009-04-18
```
sudo apt-get -f install
```

or 

```
sudo apt-get install libgnomedesktop2.20-cil libnotify0.4-cil librsvg2-2.18-cil libwnck2.20-cil
```

Of course you must have **universe** repository open.If you don´t go to the system>admin>software sources and there check universe and multiverse.Refresh and you can install desired packages.

---

