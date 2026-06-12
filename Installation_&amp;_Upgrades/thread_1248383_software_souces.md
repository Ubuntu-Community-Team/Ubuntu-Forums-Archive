---
title: "software souces"
date: 2009-08-24
forum: Installation &amp; Upgrades
---

### Post by johnh10000 on 2009-08-24
Hi gang, I needed rar and unrar.  A quick google search, gave them to me, via
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

How can a make this for jaunty be in my sources list?

---

### Post by junke1990 on 2009-08-24
you dont have to just install the package called RAR

```
sudo apt-get install rar
```

---

### Post by ibutho on 2009-08-24
You need to enable the multiverse and universe repositories then do
```
sudo apt-get install unrar
```
or
```
sudo apt-get install unrar-free
```

---

### Post by sisco311 on 2009-08-24
Go to *System -> Administration -> Software Sources* and make sure that the multiverse repository is enabled, then install the packages via Synaptic, Add/Remove, apt-get or apturl (click):
[rar](apt://rar)
[unrar](apt://unrar)

---

