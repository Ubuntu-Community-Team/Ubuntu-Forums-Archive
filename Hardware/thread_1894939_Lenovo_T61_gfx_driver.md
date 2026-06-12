---
title: "Lenovo T61 gfx driver"
date: 2011-12-13
forum: Hardware
---

### Post by hvidehenning on 2011-12-13
i cant seem to install any driver for my gfx on my Lenovo T61 does anybody know any working driver for this problem (ubuntu x64 v.11.10)

---

### Post by Mark Phelps on 2011-12-14
Are you seeing a desktop? IF so, the default Intel drivers have already been installed as part of the initial setup.  

Unlike with Windows, in Linux, you don't start scurrying around for drivers after you install the OS.

---

### Post by hvidehenning on 2011-12-19
> **Mark Phelps said:**
> Are you seeing a desktop? IF so, the default Intel drivers have already been installed as part of the initial setup.  

Unlike with Windows, in Linux, you don't start scurrying around for drivers after you install the OS.

all things works but it cant find the intel chip so i cant use  ex. wine or alien arena

---

### Post by MoreOrLess on 2011-12-19
What is the output of glxinfo?
```
sudo apt-get install mesa-utils
glxinfo
```

---

