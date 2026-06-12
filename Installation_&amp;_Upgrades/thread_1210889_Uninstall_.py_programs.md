---
title: "Uninstall .py programs"
date: 2009-07-12
forum: Installation &amp; Upgrades
---

### Post by villalcalde84 on 2009-07-12
I'm using Ubuntu 8.04 and I would like to install the latest version of Mitter, the Twitter desktop client. I already have the version 0.3.2.2 installed through a .deb package I found in [Getdeb.net]("http://www.getdeb.net/app/Mitter"), but I would like to have version 0.4.5.

I downloaded the .tar.gz package from its home page, and found that to install it I have to run the comand:
```
sudo python setup.py install
```

I have not installed software this way, and my question is, if I install Mitter this way, ¿how do I remove it if I want to later? ¿Is there an easy way to do it? ¿Is there a way to convert it into a .deb package for easy installation/removal procedure?

Thanks in advance.

---

### Post by Partyboi2 on 2009-07-12
Hi, you could use checkinstall to create  a deb package, that way it will be easy to remove if you need to.
```
sudo apt-get install checkinstall
```Once installed change into the mitter source directory and
```
sudo checkinstall python setup.py install
``` then answer the few questions and a deb package should be created that you can install with
```
sudo dpkg -i mitter_0.4.5-1_i386.deb
```

---

### Post by villalcalde84 on 2009-07-12
Thanks Partyboi2, it worked! Now I have the latest version of Mitter installed :D

---

