---
title: "Installing wireless USb dongle driver?"
date: 2010-09-03
forum: Hardware
---

### Post by lobfredd on 2010-09-03
Hello.
I have a Realtek RTL8188SU wireless USB dongle and i need to install the driver to get it work.
There is a linux driver on the disc but i dunno how to install it :P
pls help :D

---

### Post by IcarusR on 2010-09-03
Are we talking about the realtek supplied cd ??
The driver will either be a .deb, in which case double click to install. Or a .tar, double click to unpac it, then navigate to the expanded directory & read through any readme.txt or install.txt files for instructions.
In the case of the latter you will first need to install the build essential package, this contains the compiler etc. In a terminal type..

```
sudo apt-get install build-essential
```

---

### Post by lobfredd on 2010-09-03
> **IcarusR said:**
> Are we talking about the realtek supplied cd ??
The driver will either be a .deb, in which case double click to install. Or a .tar, double click to unpac it, then navigate to the expanded directory & read through any readme.txt or install.txt files for instructions.
In the case of the latter you will first need to install the build essential package, this contains the compiler etc. In a terminal type..

```
sudo apt-get install build-essential
```

It contains a .tar.gz with the files shown in the picture.

---

### Post by lobfredd on 2010-09-04
bump

---

