---
title: "Sun JDK Path Problem"
date: 2005-12-12
forum: Installation &amp; Upgrades
---

### Post by mrdhinesh on 2005-12-12
Hi 
 I am new to Linux and like to start my java development in Ubuntu.

Just I am briefing the problem which I am facing below:

I tried installing sun Java but still Ubuntu 5.10 point to a Java version which comes bundled with Ubuntu...I need the defaut java to be one which I have installed.How to achive this? when I try to uninstall the bundled Java using package manager it is forcing me to uninstall OpenOffice also.

Thanks
Dhinesh

---

### Post by wylfing on 2005-12-12
Try this:
```
sudo update-alternatives --config java
```
Then pick something other than GIJ.

---

