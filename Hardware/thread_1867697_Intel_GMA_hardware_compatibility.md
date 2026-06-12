---
title: "Intel GMA hardware compatibility"
date: 2011-10-23
forum: Hardware
---

### Post by Harry.k on 2011-10-23
Hey. I have an old pc, which had winduhs xp, which i recently replaced with Natty. The problem is that opengl based games run slower than they did in winduhs. DirectX would be slow when emulated through wine, and is understandable. But why do linux native OpenGL games (like frets on fire, for instance) lag compared to winduhs? Am i missing any drivers or something??

---

### Post by Harry.k on 2012-03-05
A modified xorg.conf improved the performance, but games like warsow which is native on win and lin still look pathetic in ubuntu compared to windows. I really dont want to go back to that virus filled os. Is there anything that can be done to fix this?

---

### Post by Harry.k on 2012-03-20
Ba-bump

---

### Post by Torgas Prim on 2012-03-20
Best option is to look up your model and manufacturer here: [http://www.linux-laptop.net/](http://www.linux-laptop.net/)
and use the distro that has been found to work best on it.

---

### Post by Yellow Pasque on 2012-03-20
How old of a PC are we looking at? What GPU do you have?
```
lscpi
```

---

### Post by Harry.k on 2012-03-22
Intel 82845G/GL[Brookdale-G]/GE chipset. Speaking in computer years, it is prehistoric. Although, it ran most last-gen games smoothly. Even gta sa ran reasonably. So i'm guessing it is not a hardware issue

---

### Post by Yellow Pasque on 2012-03-22
i8xx chip? That's what I thought :/
[https://wiki.ubuntu.com/X/Bugs/Mavericki8xxStatus](https://wiki.ubuntu.com/X/Bugs/Mavericki8xxStatus)

---

### Post by Harry.k on 2012-03-23
Been there, done that. Stuff worked fine in natty. In fact, this worked perfectly in natty. One of the earlier daily builds of oneric even ran unity 3d, albeit without the xorg.conf. However precise and the up-to date oneric only run unity 2d. No 3d games work either

---

### Post by Yellow Pasque on 2012-03-23
Post/pastebin your /var/log/Xorg.0.log

---

### Post by Harry.k on 2012-03-25
Sorry it took so long. Here you go. Extreme tux racer runs smoothly on all the versions smoothly. strange...:confused:

---

### Post by Harry.k on 2012-03-25
Bump

---

### Post by Harry.k on 2012-03-30
Bump

---

### Post by Yellow Pasque on 2012-03-30
Log looks fine.. *shrug

---

