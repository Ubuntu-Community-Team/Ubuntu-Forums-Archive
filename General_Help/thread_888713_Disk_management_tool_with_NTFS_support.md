---
title: "Disk management tool with NTFS support"
date: 2008-08-13
forum: General Help
---

### Post by SandyM on 2008-08-13
I am using windows as well as Linux. Currently I am facing some critical problems with windows and I think I can only correct them through ubuntu.

Please tell me if there is any efficient disk management tool for ubuntu also tell me commands to format ,merge and create new disk and other important related commands as well as procedures if possible.

---

### Post by Nepherte on 2008-08-13
Did you try gparted?

---

### Post by tfosorcim on 2008-08-13
Gparted and ntfsprogs.

---

### Post by Sycron on 2008-08-13
> **SandyM said:**
> I am using windows as well as Linux. Currently I am facing some critical problems with windows and I think I can only correct them through ubuntu.

Please tell me if there is any efficient disk management tool for ubuntu also tell me commands to format ,merge and create new disk and other important related commands as well as procedures if possible.

You may try **gparted**. Install it with:
```
$ sudo apt-get install gparted
```
and run it:
```
$ sudo gparted
```
If you can't install it you may have to uncomment the universe repositories from **/etc/apt/sources.list**.

---

