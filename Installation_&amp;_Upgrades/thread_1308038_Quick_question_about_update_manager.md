---
title: "Quick question about update manager"
date: 2009-10-31
forum: Installation &amp; Upgrades
---

### Post by LiamG on 2009-10-31
If I download a 10 meg software update, do those 10 megs get added to the program or do they replace a part of it? I'm trying to work out whether or not I am slowly filling up my hard disk with updates. Does anybody know?

---

### Post by Bucky Ball on 2009-10-31
Quick answer: it can vary. Usually replace but sometimes add a new feature. Generally, no, they don't expand much. If you have 6 Gb of apps it will remain pretty much that unless you add more (new) apps. Adding new packages is going to grow the data, naturally.

---

### Post by grandtoubab on 2009-10-31
[]("https://help.ubuntu.com/8.04/serverguide/C/apt-get.html")[http://www.debian.org/doc/manuals/apt-howto/](http://www.debian.org/doc/manuals/apt-howto/)

So clean your packages before upgrade
sudo apt-get autoclean
sudo apt-get clean


or use the graphical tool computer janitor
System -> Administration -> system Cleaning  (I am french I try to translate the menu, it is that one with the brush)

---

