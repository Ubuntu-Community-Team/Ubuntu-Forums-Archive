---
title: "Force reinstallation of Intel drivers"
date: 2009-03-12
forum: Hardware
---

### Post by seppl82 on 2009-03-12
Hi all,

problem: I've booted my ubuntu on another machine

now: The graphics driver is no longer compatible to my graphics card. Using default driver

todo: Performance leak... no 3D acceleration...

What shall i do ?

---

### Post by seppl82 on 2009-03-13
Okay,

sudo dpkg-reconfigure -phigh xserver-xorg

logout

[CTRL] + [ALT] + [BACKSPACE]

login

=> SOLVED!

THANKS!

---

