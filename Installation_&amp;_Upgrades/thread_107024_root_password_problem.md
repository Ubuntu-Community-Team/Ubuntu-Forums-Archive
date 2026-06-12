---
title: "root password problem"
date: 2005-12-22
forum: Installation &amp; Upgrades
---

### Post by gnome on 2005-12-22
**hi dears. **

during the installation of Ubunty (dont rem-r the vers) i couldnt enter root password. just created the single user and enterd thge system. then i heared that in expert installation mode root exists. 

in standard isntall mode there is no root password. 

my quiestion is why is that?

thank u

---

### Post by 23meg on 2005-12-22
It's Ubuntu's policy to disable the root password by default. It's encouraged that you use sudo instead.

[http://wiki.ubuntu.com/RootSudo](http://wiki.ubuntu.com/RootSudo)

You can enable the root account with ```
sudo passwd root
```

---

