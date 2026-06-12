---
title: "536ep patched driver for feisty"
date: 2007-03-29
forum: Hardware &amp; Laptops
---

### Post by mrgibson on 2007-03-29
I was unable to compile 536ep drivers to feisty since the last kernel changed how DECLARE_WORK function work. I created a quick&dirty patched version of the source code, you can grab it there: 

[http://www.mrgtech.ca/intel_536ep_feisty.tar.gz](http://www.mrgtech.ca/intel_536ep_feisty.tar.gz)

now its compile and work just fine (2.6.20-13-generic) I also left the Intel536.ko in the directory for lazy people, just do a `sudo make install` (if you have the same kernel version)

Hope it help

Yanick Bourbeau

---

### Post by Swab on 2007-04-03
Thanks for this, most helpful!

---

