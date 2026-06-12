---
title: "Need help with Wine"
date: 2009-09-12
forum: Installation &amp; Upgrades
---

### Post by drewkros1184 on 2009-09-12
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I need help installing Wine on my computer, i keep getting the above command prompt everytime I do. My friend didn't have Windows so when he fixed my computer he put Ubuntu on it but I can't for the life of me figure out how to work it. Can anyone help?

---

### Post by ahbart on 2009-09-12
Open a terminal (menu - accessories - terminal window) and type 
```
sudo dpkg --configure -a
```
type your password when prompted. That's what apt (package manager) is telling you.

---

### Post by khelben1979 on 2009-09-12
If you have any more problems you should also take a look at [the Wine wiki page]("http://wiki.winehq.org/").

---

