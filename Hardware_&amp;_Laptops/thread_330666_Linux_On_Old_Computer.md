---
title: "Linux On Old Computer"
date: 2007-01-03
forum: Hardware &amp; Laptops
---

### Post by jay81 on 2007-01-03
I have an old PC with the following spec:

Intel Celeron 433MHz CPU
64Mb RAM
6Gb Hard Disk
Intel 810 Video & Sound
CD & DVD Drives

I currently have Windows 2000 installed on this, other than it being a bit slow due to the lack of memory, Win2K runs alright.

What Linux distribution would you guys recommend?  I have tried using the Ubuntu live CD, with no luck.  I am not sure weather this is down to the lack of memory, or the on-board video adapter not being supported.

I have tried Xubuntu which was OK but a little slow.

---

### Post by az on 2007-01-03
Windows 2000 will run faster than any current linux OS on that hardware.  DSL (Damn Small Linux) will probably work out the best.

The live cd did not work because of the ram.  Your onboard video should work just fine.

---

### Post by pormogo on 2007-01-03
I would look at the small distros like DSL and Knoppix here. Fluxbox IMO is a nice windows manager for machines that are a little low on resources.

---

### Post by c.dric on 2007-01-03
I'm guessing you want to use the computer as a desktop computer, in such case i think xubuntu is your best option ... maybe with some added ram. (If you tried with LiveCD it's likely to be slow ... you should try an install to get an idea of the real speed)

There are other light desktops that you could use instead of xfce but i have no idea if they're so much lighter.

Any way 64mb is a little tight for a multimedia desktop, whatever the desktop you use.

If you want to make a server that's a different story. I used to have a router running linux with a P133 and 24mb of ram so ... :)

---

### Post by finferflu on 2007-01-03
I would suggest to use xubuntu alternate CD install, and then install IceWM as Windows Manager, it's very very (I mean very) fast. 

to install it, after you install xubuntu, run 

```
sudo aptitude install icewm icewm-themes
```

Even though IceWM looks horrible to start with, you can make it very nice and eyecandy.

---

### Post by raul_ on 2007-01-03
> **azz said:**
> Windows 2000 will run faster than any current linux OS 

I'm sorry? :rolleyes: 

Anywayz, DSL and Puppy Linux seem to be the best. Check this list:

[http://en.wikipedia.org/wiki/MiniLinux]("http://en.wikipedia.org/wiki/MiniLinux")

---

### Post by heartwort on 2007-01-03
> **raul_ said:**
> I'm sorry? :rolleyes: 

Anywayz, DSL and Puppy Linux seem to be the best. Check this list:

[http://en.wikipedia.org/wiki/MiniLinux]("http://en.wikipedia.org/wiki/MiniLinux")


I used Puppy Linux on an old computer.  Worked great though I did have more RAM than jay81.  I think the goal for Puppy is to keep it down to @ 50 MB.  I couldn't install it because it requires DOS which I didn't have, but I've heard it's an easy hard drive install which would probably be better with so little RAM.  Than again, RAMs pretty cheap these days.

---

