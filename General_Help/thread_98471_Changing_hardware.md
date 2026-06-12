---
title: "Changing hardware"
date: 2005-12-03
forum: General Help
---

### Post by k3nv on 2005-12-03
If I have Ubuntu installed on one system and I upgraded the mobo, cpu, video card, would I need to do a re-install?  Basically swap HD into another computer.  I remember doing this with Slackware a long time ago and it had no problems.

---

### Post by teaker1s on 2005-12-03
make sure you have the right kernel and restricted modules installed for cpu

you may need to 
sudo dpkg-reconfigure xserver-xorg

and you may need different driver for graphics card if that's changing

---

### Post by k3nv on 2005-12-03
[QUOTE=teaker1s]make sure you have the right kernel and restricted modules installed for cpu

you may need to 
sudo dpkg-reconfigure xserver-xorg

and you may need different driver for graphics card if that's changing[/QUOTE]

Thanks

---

