---
title: "I have a separate /home partition. How to clean install?"
date: 2009-02-11
forum: Installation &amp; Upgrades
---

### Post by JazonEsti on 2009-02-11
I am currently using Kubuntu 8.04. I have a separate /home partition, and I wish to clean install Kubuntu 8.10. I read that having a separate /home partition preserves settings and such, but should I do something to easily restore them (i.e. Firefox bookmarks, amarok playlists etc).

Also, can my hardware handle Kubuntu 8.10?
Athlon XP 2400+
256 MB RAM
GeForce 2 MX 400.

I'm a bit worried KDE 4.1 (can  upgrade to 4.2?) might slow down my PC.  

Thanks!

---

### Post by x33a on 2009-02-11
well if you want the best performance out of your hardware, i would suggest xubuntu or even ubuntu would do fine. but kubuntu is likely to slow you down.

as for partitioning, since you have a separate /home partition you don't have to do anything further. the data will be automatically read.

---

### Post by acracker on 2009-02-11
If you're worried about speed, I would use KDE 3.5 instead of 4.x. I tried out Kubuntu 8.10 for a few months but I found it to be full of bugs and quirks. It looked nice, sometimes, but often times the graphics would screw up for no reason or it would just freeze :(
I've heard that KDE 3.5 is much more stable and reliable, so I'd go with that if I were you. Or, you could switch to regular Ubuntu ;)

---

### Post by JazonEsti on 2009-02-23
Great! Thanks guys! What about drivers? I manually installed HP DJ2560's drivers before. Do I need to reinstall it?

Also, will the same advantage (settings importation) work with Linux Mint?

Thanks again!

---

### Post by SuperSonic4 on 2009-02-23
Firefox bookmarks are stored in ~/.mozilla and amarok playlists are stored in ~/.kde/share/apps/amarok/ so keeping /home will preserve both of them as well as other things (firefox addons for example)

I think an ubuntu server install would be best on your system, then you can install whichever packages you want (like kde-core for a minimal kde install)

If you want to keep /home separate you'll need to reassign it by manually editing the partitions and ensuring you **do not reformat**

---

### Post by JazonEsti on 2009-02-24
Thanks for the warning. 

How about the HP driver? Will it be intact? Thanks!

---

### Post by JazonEsti on 2009-02-25
Bump.

How about the drivers? Will they be intact? Thanks!

---

