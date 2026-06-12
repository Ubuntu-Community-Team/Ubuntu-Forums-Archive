---
title: "How to get proper screen resolution"
date: 2008-09-23
forum: General Help
---

### Post by Robotman on 2008-09-23
Hi all,
I just installed Xubuntu 8.04 on a partition of my HD.  I use Ubuntu 7.10 on this same machine and can get a screen resolution of 1600x1200 using the restricted Nvidia driver.
When I installed the restricted Nvidia driver on the Xubuntu partition however, the only option I see for screen resolution is a paltry 320x400.  That's just unusable.
How can I get 1600x1200 screen resolution for my Xubuntu partition?

---

### Post by tuxxy on 2008-09-23
Did you install nvidia-settings

---

### Post by cariboo on 2008-09-23
You could also try in a terminal:

```
sudo displayconfig-gtk
```

This will set up your display in /etc/X11/xorg.conf

Jim

---

### Post by Robotman on 2008-09-24
Thanks Jim, that worked after I specified what make of monitor I use. :D

---

