---
title: "Installation backup with all settings"
date: 2009-06-04
forum: Installation &amp; Upgrades
---

### Post by ubila on 2009-06-04
Hello all :D

Im rather new to Ubuntu, so far loving it!
Ive installed it on a few of my home machines, and configured them all with the "Perfect Server Guides" - So far everythings running perfect!

I was curious to know if once i have installed Ubuntu and set it up with additional installs/programs + settings, is there a way to then "backup" a "snapshot" of that machine?
So that if i want to install it exactly the same on another machine i can without adding all the additional installs + settings manualy?

This might be covered somewere else,  sorry if i missed the thread.

Cheers

---

### Post by jerrrys on 2009-06-04
if you want a clone...

[http://clonezilla.org/](http://clonezilla.org/)

---

### Post by utnubuuser on 2009-06-04
clone the hdd. gparted will copy an entire disk, or just a partition.

---

### Post by dje on 2009-06-04
use [SystemRescueCd]("http://www.sysresccd.org/Main_Page") and partimage to image your drive or use [Clonezilla]("http://clonezilla.org")

dje

---

### Post by jerrrys on 2009-06-04
> **utnubuuser said:**
> clone the hdd. gparted will copy an entire disk, or just a partition.

it will ??

---

### Post by ubila on 2009-06-04
Thanks for the replys :D
Ill check out clonezilla first off :D

---

### Post by pawnrocket on 2009-06-04
Another option. If you are using most of these systems in your home and you have one fast system you could setup the LTSP Server and just connect them all over your network. 

Server 1 stores the desktop of any user you want

On boot up you choose network boot and it seeks out then finds the Linux Terminal Server. 

You get your OS over the network. All changes stay there. The benefits are that if your other machines have very old hardware it doesn't much effect them. They need only have a strong Network connection.

---

### Post by utnubuuser on 2009-06-09
Eye Will

---

