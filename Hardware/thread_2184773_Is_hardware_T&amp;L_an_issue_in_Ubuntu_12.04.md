---
title: "Is hardware T&amp;L an issue in Ubuntu 12.04"
date: 2013-10-30
forum: Hardware
---

### Post by acodea on 2013-10-30
The  question is, is Hardware T and L supported in Ubuntu? My computer is updated with the best drivers and have had SNA enabled on them. GLX is working. The question is for gaming and high performance computing. I want to install wine and Chrome VG, and it requires Hardware T and L. I have Gnome3d installed.

Something happened and the post I made disappeared. So this had to appear as a scribbled note. 

Xorg Drivers and glxinfo are below.


```
ooboo@ubuntu:~$ grep Graphics /var/log/Xorg.0.log
[    38.938] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
    Ivybridge Server (GT2), HD Graphics, HD Graphics 4600,
    Haswell Desktop (GT3), HD Graphics, HD Graphics 4600,
    Haswell Mobile (GT3), HD Graphics, HD Graphics P4600/P4700,
    HD Graphics, Haswell (GT2), Haswell (GT3), Haswell SDV Desktop (GT1),
    Iris(TM) Graphics 5100, HD Graphics, HD Graphics 4400,
    HD Graphics 5000, Haswell ULT Server (GT1), Haswell ULT Server (GT2),
    Iris(TM) Graphics 5100, Haswell ULT (GT1), Haswell ULT (GT2),
    Iris(TM) Graphics 5100, HD Graphics, HD Graphics 4200,
    Iris(TM) Graphics 5100, Haswell CRW Desktop (GT1), HD Graphics 4600,
    Iris(TM) Pro Graphics 5200, Haswell CRW Mobile (GT1),
    HD Graphics 4600, Iris(TM) Pro Graphics 5200,
    Iris(TM) Pro Graphics 5200, Haswell CRW (GT1), Haswell CRW (GT2),
    Iris(TM) Pro Graphics 5200, Haswell CRW (GT1), Haswell CRW (GT2),
    Iris(TM) Pro Graphics 5200, ValleyView PO board
[    38.972] (--) intel(0): Integrated Graphics Chipset: Intel(R) GM45

ooboo@ubuntu:~$ glxinfo | grep "OpenGL version"
OpenGL version string: 2.1 Mesa 9.1.4

```

---

### Post by Yellow Pasque on 2013-10-31
Any modern GPU should support it.

---

### Post by acodea on 2013-10-31
I thought this would be one that everyone is interested in.

---

### Post by Yellow Pasque on 2013-10-31
> **acodea said:**
> I thought this would be one that everyone is interested in.

???

---

### Post by acodea on 2013-10-31
> **Temüjin said:**
> ???


yeah; well, there is so big a market in videocards, I thought everyone had an itch to find out the features of their ever more complicated card or gpu, and a quorum would be called on the subject. lol

---

