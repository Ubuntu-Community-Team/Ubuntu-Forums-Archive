---
title: "cd emulation software and other help"
date: 2008-11-12
forum: General Help
---

### Post by MillionFlame on 2008-11-12
sup folks im really new to linux(less than a week of it being on my system!) and i was wondering about running cd emulation on it. i have alot of iso's on my windows partition and i was used to just using daemon tools to runin it. is there anything of the sort u guys can point me too?

also, if by any chance would would be the best bet for me to more familiarize my self with this OS? it took me a week to finally figure out
how to install the damn locked nvidia driver hahaha.

also how to beter use the command line?

thanks alot any help at all would be appreciated

---

### Post by taurus on 2008-11-12
If you want to mount an ISO file without burning it first, just do

Applications -> Accessories -> Terminal
```
sudo mkdir /media/iso
sudo mount -t iso9660 *filename.iso* /media/iso -o loop
```

---

### Post by bodhi.zazen on 2008-11-12
There are a few gui tools to do this for you as well.

You could try gmountiso (sudo apt-get insall gmountiso), although there are others as well.

---

