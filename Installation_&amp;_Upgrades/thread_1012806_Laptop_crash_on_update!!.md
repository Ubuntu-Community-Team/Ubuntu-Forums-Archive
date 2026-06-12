---
title: "Laptop crash on update!!"
date: 2008-12-16
forum: Installation &amp; Upgrades
---

### Post by Zip247 on 2008-12-16
Today my laptop crashed while in the middle of an update.  Only one update was coming in, it was the ubuntu-docs 8.06.1.  After restarting my pc and trying to run the updater again it told me I had to use command line and enter "dpkg --configure -a".  

Can someone tell me what this does.

---

### Post by taurus on 2008-12-16
Close the update-manager window first.  Then, open a terminal and run

Applications -> Accessories -> Terminal
```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
```

---

