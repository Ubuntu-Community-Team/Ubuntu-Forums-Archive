---
title: "Compiz conflict between plugins-extra and plugins-unofficial"
date: 2009-04-11
forum: Installation &amp; Upgrades
---

### Post by weezilla on 2009-04-11
First off, this is my first post, so hello all !

I'm running 8.10 Gnome.

 Okay, I've been fighting with ubuntu for many hours trying to get the compiz-plugins-unofficial package to install. I've tried uninstalling compiz completely and reinstalling, but even if I remove all the compiz packages under the syanptics manager, compiz and two dependencies of it still run in the processes manager, but freeze the interface if I close them. 

After installing compiz (sudo apt-get install compizconfig-settings-manager compiz-fusion-plugins-extra compiz-fusion-plugins-main compiz-plugins emerald ||| to be exact), I try installing the compiz-plugins-unofficial package to get the way cool effects. When I do this, I get this error.

E: /var/cache/apt/archives/compiz-fusion-plugins-unofficial_0.0.2~git20070921+3v1ubuntu0_i386.deb: trying to overwrite `/usr/lib/compiz/lib3d.so', which is also in package compiz-fusion-plugins-extra

I've tried backing up and deleting lib3d.so, but that doesn't remedy it. I've tried removing compiz-fusion-plugins-extra and adding compiz-plugins-unofficial, but I get a varied error message of the same flavor (different files though). 

I'm not very good with linux, but I suspect I may have two compiz installs. Does compiz come default with Ubuntu Gnome 8.10?

Just a note, I also have AWN installed. Not sure if that matters.

If anything, I would greatly appreciate help on navigating linux to fix this problem (I realize the unofficial package is...unofficial).

Thanks so much !!!
Weezilla

---

### Post by weezilla on 2009-04-11
bump of desparation

---

