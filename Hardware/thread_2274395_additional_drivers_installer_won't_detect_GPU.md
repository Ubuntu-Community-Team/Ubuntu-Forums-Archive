---
title: "additional drivers installer won't detect GPU"
date: 2015-04-20
forum: Hardware
---

### Post by Harry.k on 2015-04-20
A friend of mine installed Ubuntu on his Dell inspiron 15 3000 series laptop with Intel 4000 and nvidia 820m GPUs. The glmark scores show that the Intel GPU is being used. The additional drivers utility doesn't show the nvidia GPU. I tried installing binary drives manually, but that messed up the system. Unity wouldn't start, and trying to start glmark from awesome gives errors. I have since restored the Intel drivers and brought things back to the way it was. Is there any way to get the nvidia GPU working in Ubuntu?

---

### Post by dino99 on 2015-04-20
the 820m needs the 349 driver (pick it from xorg-edgers ppa, install it then disable the ppa) but first purge (sudo apt-get purge nvidia*) the installed one, then install the ppa one

---

### Post by Harry.k on 2015-04-28
That worked. Thanks. Unfortunately, i forgot to disable the ppa and he updated the system XD

---

