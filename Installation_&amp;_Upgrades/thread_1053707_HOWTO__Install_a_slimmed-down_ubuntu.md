---
title: "HOWTO:  Install a slimmed-down ubuntu"
date: 2009-01-28
forum: Installation &amp; Upgrades
---

### Post by karvec on 2009-01-28
Download the ubuntu minimal CD from:  

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

Follow the simple text-based installer, then do a:

sudo apt-get install xorg gnome-core

and it will install the bare minimums for Gnome and cut out a *LOT* of extras!!  You can install the entire ubuntu package by 

sudo apt-get install ubuntu

But that would betray the entire point of installing gnome without all the extras.


Also, you can install kde, xfce, and pretty much any of the other ones and cut out all the extras by doing the same thing.

I found the speed difference in the base install much faster and smoother than the entire bloated Ubuntu package.

---

### Post by kerry_s on 2009-01-29
minimal, dump the desktop altogether.

sudo apt-get install xorg lxde

i prefer:
sudo apt-get install xorg jwm pcmanfm leafpad xfce4-icon-theme lxapperance

---

