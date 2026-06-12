---
title: "Monitor has low resolution"
date: 2011-02-18
forum: Hardware
---

### Post by emperor_mai on 2011-02-18
Hi, I'm new to Ubuntu. I have version 10.04 and installed it from a disk. Everything was working fine yesterday but today I logged on and my monitor resolution was low. I looked into monitor preferences and it said my Monitor was unknown, and my resolution maxes out at 1024 x 768. If it's relevant my graphics card is an S3 Unichrome model. I poked around but nothing really seems to be helping or directions are just too technical for me. Any ideas?

---

### Post by sikander3786 on 2011-02-18
Welcome to the forums :-)

Try reconfiguring your graphics.

From Applications > Accessories > Terminal:

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```

Note capital 'X' for X11. It is says file not found, no problem. Proceed to the next one.

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Reboot.

```
sudo reboot now
```

Let us know how that goes.

---

