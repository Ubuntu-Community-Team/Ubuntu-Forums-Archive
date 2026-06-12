---
title: "Difficulties with Dual Install, Xubuntu 8.10 and Musix 1.0.0"
date: 2009-04-13
forum: Installation &amp; Upgrades
---

### Post by translucent juicebox on 2009-04-13
I'm trying to do a dual boot with xubuntu linux and musix linux, xubuntu for general purpose, and musix for recording and producing music.  I already have musix installed, but when I start installing xubuntu, I can't because the partitioner can't detect that I already have an OS installed, my only option is to use the entire harddrive for xubuntu without musix.  When I try to do a manual partition, the partitioner says that the amount of data in the partition where musix is, is unknown.  And the partitioner won't allow me to resize the musix partition, and create a separate one for xubuntu.  

Why can't xubuntu recognize that I already have an OS installed and how do I solve this problem?

---

### Post by Elfy on 2009-04-13
Not sure about the xubuntu livecd - look for PArtition Editor in the System menus.

That will open gparted and you can resize and create a partition before you start the installer.

IF you can't find it in the menus - start it from terminal

```
gksudo gparted
```

---

