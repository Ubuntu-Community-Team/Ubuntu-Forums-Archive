---
title: "screen and monitor not matching"
date: 2009-05-05
forum: Installation &amp; Upgrades
---

### Post by Ampi on 2009-05-05
I just installed Ubuntu 9.04 on my laptop (Toshoba Satellite) it's the first time I'm using a laptop so there is a lot I don't know.
The screen and monitor don't seem to match in size. 
The biggest resolution I can choose is around 800x600 and that still leaves a big part of the screen blank (black).
Any idea how I can change this (I'm used to the bottons on the monitor ;))

---

### Post by wpshooter on 2009-05-05
**TO ME**, the easy solution to this would be to re-install Ubuntu from the ALTERNATE CD version of Ubuntu instead of using the desktop version of Ubuntu.

---

### Post by Ampi on 2009-05-05
Is that really the only solution??? Because with this laptop, I do not know what it is, it already took me so long to install Ubuntu, I'm glad I already have it working now! :(
Also, I never heard of an Alternate CD, what is that?

P.S. Is it possible btw to install the netbook remix on my laptop, my laptop is meant for only internet and no huge programs, for that I use my dekstop...?

---

### Post by Mark Phelps on 2009-05-05
You can try to manually select a monitor and resolution by opening a terminal and entering "sudo displayconfig-gtk".

---

### Post by Ampi on 2009-05-06
when I try sudo displayconfig-gtk, I get command nog found...

---

### Post by Ampi on 2009-05-07
I found the solution, finally I have an "entire screen"!

I found the correct way to configure xorg.conf and now it is all good!

---

### Post by wmatheney on 2009-08-24
> **Ampi said:**
> I found the solution, finally I have an "entire screen"!

I found the correct way to configure xorg.conf and now it is all good!

I have the same problem. What is the solution?

---

