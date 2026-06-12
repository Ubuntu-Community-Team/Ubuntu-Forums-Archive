---
title: "can't install g++"
date: 2009-10-15
forum: Installation &amp; Upgrades
---

### Post by chamithmalinda on 2009-10-15
I tried to install g++ in ubuntu 9.04 following error message coming. Also i tried using synaptic there is no g++.  



[LIST=1]
[*][COLOR=Red]**lbs3@lbs3-desktop:~$ sudo apt-get install g++;**[/COLOR]
[*][COLOR=Red]**Reading package lists... Done**[/COLOR]
[*][COLOR=Red]**Building dependency tree       **[/COLOR]
[*][COLOR=Red]**Reading state information... Done**[/COLOR]
[*][COLOR=Red]**E: Couldn't find package g**[/COLOR]
[/LIST]
:(

---

### Post by lloyd_b on 2009-10-15
Try this:```
sudo apt-get install build-essential
```This will install g++, as well as a load of other utilities required to have a working build system.

Note: the package "g++" *is* in the repos, so if Synaptic isn't showing it, then something is wrong with your apt configuration...

Lloyd B.

---

