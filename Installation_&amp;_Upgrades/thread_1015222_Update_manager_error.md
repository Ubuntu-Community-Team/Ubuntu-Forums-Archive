---
title: "Update manager error"
date: 2008-12-18
forum: Installation &amp; Upgrades
---

### Post by sph0600069 on 2008-12-18
When clicking on the Install Updates button a window appears saying:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

When trying to run the command through the terminal superprivilege is riguired and I don't know hoe to continue since I am new to ubuntu

Thanks in advance

---

### Post by donkyhotay on 2008-12-18
First close the updater  program. Then go to applications > accessories > terminal
in the terminal type in:
```
sudo dpkg --configure -a
```
then try running the updater again.

---

