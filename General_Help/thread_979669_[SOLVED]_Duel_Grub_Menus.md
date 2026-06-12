---
title: "[SOLVED] Duel Grub Menus"
date: 2008-11-12
forum: General Help
---

### Post by kg87 on 2008-11-12
Ok, So its not really a serious issue but its kind of irratating

i installed heron with wubi and all was good, then i messed up the ubuntu installation, and uninstalled it via Windows (XP).

I've since installed Intrepid from liveCD and all is working great but i've got a bit of a problem, in which im given two grub menus.

the first one allows me to select intrepid, and previous kernels and then at the bottom, XP.

once XP is selected, Im then given a second grub menu, with just XP and the redundant heron. 

the question is, how the hell do i get rid of the second menu?? :confused:

thanks in advance

kg87

---

### Post by caljohnsmith on 2008-11-12
Sounds like for some reason your boot.ini file in Windows wasn't restored to its original state after uninstalling Ubuntu 8.04. When you boot into Windows, you can modify your boot.ini file via these [instructions]("http://support.microsoft.com/kb/289022") from the Microsoft website, and all you need to do is remove the line in that file that has:
```
C:\wubildr.mbr="Ubuntu"
```
Let me know how that goes. :)

---

### Post by kg87 on 2008-11-12
You legend!!!!

all sorted now, 

I was thinking i'd have to edit grub, and like i once was with window's registry, petrified of grub!! :P

---

### Post by caljohnsmith on 2008-11-12
Glad to hear you were able to fix your boot.ini file; sometimes modifying system files isn't too big of a hassle. Cheers and have fun with Intrepid. :)

---

