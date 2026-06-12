---
title: "Ati Radeon 9250"
date: 2008-01-10
forum: Hardware &amp; Laptops
---

### Post by mostafamehiri on 2008-01-10
i couldn't install the Ati driver when i try it looks like this in the terminal screen
[[img]http://img2.freeimagehosting.net/uploads/th.6f97485ae0.png[/img]](http://img2.freeimagehosting.net/image.php?6f97485ae0.png)

and when i try 2 enable 3d effects the screen turns to white and i can't do any thing
Sooo please Help me

---

### Post by eggdeng on 2008-01-11
Which version of Ubuntu are you using? Run
```
lsb_release -a
```
in a terminal to check.
Why are you installing the drivers from source? It is usually better to install from the repos.

---

### Post by Yellow Pasque on 2008-01-11
What version of the ATI driver are you trying to install?
The Radeon 9250 should use the included "radeon" driver, not any restricted/fglrx drivers.

---

