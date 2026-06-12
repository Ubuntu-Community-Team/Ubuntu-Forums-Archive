---
title: "How to find out the exact driver in use?"
date: 2013-04-01
forum: Hardware
---

### Post by Roasted on 2013-04-01
I have two identical laptops. I want to test a new wireless driver. I installed it accordingly on one of the laptops through the link I found which required a few hoops (git clone, debuild, then finally dpkg -i the .deb I built from it all). When I run lspci -v the outputs are identical. When I run lsmod, I see the "size" of the modules in use for the wireless adapter are different, which suggests one laptop has one module and the other has another, despite the fact they show up identical on lspci -v.

Is there a more definitive way to see that, yes, I am indeed running A-2013-0000-0809-1234-5678 driver on one laptop, and B-2013-0000-0809-1234-5678 on the other?

---

### Post by steeldriver on 2013-04-01
maybe

```
modinfo *modulename*
```

```
modinfo *modulename* | grep version
```

---

