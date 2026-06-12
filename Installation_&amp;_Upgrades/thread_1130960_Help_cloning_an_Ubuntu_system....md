---
title: "Help cloning an Ubuntu system..."
date: 2009-04-20
forum: Installation &amp; Upgrades
---

### Post by twgray on 2009-04-20
I have a perfectly operational Ubuntu 804 system running in my home office.  I would like to "clone" this system onto another machine, but with 810, or 904 when it is released.  By "clone" I mean I would like to have all the packages installed on the second system that I have on the 804.  So, my question is, is there a list of all installed packages somewhere on the home office system?

---

### Post by mikewhatever on 2009-04-20
I very much doubt 'cloning' is the right term for what you want. It should also be clear that packages aren't guaranteed to keep the same names form one release to the other, while also, completely new packages may be introduced and some old ones removed. It should also be mentioned that installing the same packages on the new system will not transfer any of the settings from the old one. Anyway, the following command should create a text file on your desktop with the list of all installed packages: dpkg --get-selections > ~/Desktop/all-packages

---

### Post by Cheesemill on 2009-04-20
Check out this thread:
[http://ubuntuforums.org/showthread.php?t=576629]("http://ubuntuforums.org/showthread.php?t=576629")

---

### Post by 2hot6ft2 on 2009-04-20
If all the apps you have installed were installed from the repositories then this will do what you're wanting.
> **handydan918 said:**
> Okay, this should be in the wiki, or something. It's so simple, yet so powerful.


```
sudo dpkg --get-selections
```


```
sudo dpkg --get-selections > softwarelist
```
At this point in the proceedings, you hose your system and reinstall, and then...

```
dpkg --set-selections < softwarelist
```


```
apt-get dselect-upgrade
```

Enjoy.

---

