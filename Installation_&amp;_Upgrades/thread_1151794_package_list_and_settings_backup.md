---
title: "package list and settings backup?"
date: 2009-05-07
forum: Installation &amp; Upgrades
---

### Post by Meow27 on 2009-05-07
since ive been hit with a problem that i cant seem to get help fast enough, i got this question

is there a method where i can save all of my marked packages, desktop shortcuts and panel applets?

im thinking this because i want to reinstall jaunty on my laptop, but i dont want to go over having to go through everything i want to install all over again. id rather get it all back in one shot (or 3)

is this possible?

thanks in advance
-meow

---

### Post by zvacet on 2009-05-07
Maybe you can do it with [this.]("http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html")

---

### Post by unutbu on 2009-05-07
To save a list of all installed packages:

```
dpkg --get-selections > ~/Desktop/package-list
```

To tell apt-get to reinstall all those packages:

```
sudo dpkg --set-selections < ~/Desktop/package-list
sudo apt-get update
sudo apt-get dselect-upgrade
```

To save your desktop shortcuts, backup your ~/Desktop directory.

To save your panel applets, hm... I'm not sure exactly where the panel configuration files are kept, but if you backup .config, .gconf, and .gnome2, I think all your gnome desktop settings will be saved.

---

### Post by zvacet on 2009-05-07
You can save all packages you installed via synaptic or apt with [aptoncd.]("http://aptoncd.sourceforge.net/") It is in synaptic.

---

### Post by Meow27 on 2009-05-08
> **zvacet said:**
> You can save all packages you installed via synaptic or apt with [aptoncd.]("http://aptoncd.sourceforge.net/") It is in synaptic.

that proved to be very useful. thanks ! [/solved]

---

