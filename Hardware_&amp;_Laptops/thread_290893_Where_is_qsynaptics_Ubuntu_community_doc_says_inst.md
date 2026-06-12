---
title: "Where is qsynaptics? Ubuntu community doc says install, but the packages don't exist?"
date: 2006-11-01
forum: Hardware &amp; Laptops
---

### Post by zds on 2006-11-01
I'm having the same synaptics touchpad as plenty of other people (jumpy, random left click, etc).

A Ubuntu community doc on this problem says to install qsynaptics.

So, I follow the instructions...

and get the following error message:


:/$ sudo apt-get install qsynaptics
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package qsynaptics


What the heck? Please help! My trackpad  is getting harder to control by the minute!

---

### Post by zds on 2006-11-01
found it. repositories needed to be expanded. see: 

[https://wiki.ubuntu.com/MOTU/Packages?action=show&redirect=UniversePackages](https://wiki.ubuntu.com/MOTU/Packages?action=show&redirect=UniversePackages)

remains to be seen if it solves the trackpad problem.

and people wonder why i prefer the terminal...

---

### Post by bodycoach2 on 2006-11-01
I used Synaptic to install qsynaptics, but I have to start it with the terminal.

On my laptop (not sure why they call that hotplate a 'lap' top), you have to go to qsynaptics everytime you start the computer to disable the doubletap.

> **zds said:**
> found it. repositories needed to be expanded. see: 

[https://wiki.ubuntu.com/MOTU/Packages?action=show&redirect=UniversePackages](https://wiki.ubuntu.com/MOTU/Packages?action=show&redirect=UniversePackages)

remains to be seen if it solves the trackpad problem.

and people wonder why i prefer the terminal...

---

