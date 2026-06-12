---
title: "Updating Driver"
date: 2009-03-22
forum: Hardware
---

### Post by Karisma on 2009-03-22
Hi, i am still newbie in using xubuntu. I tried to start a game titled Glest and there was an error message said that i need to update (or maybe upgrade, i am sorry i forgot it) my driver because it needs opengl 1.3. What should i do? please kindly help me:(

---

### Post by mhgsys on 2009-03-22
open a terminal 

typ
```

sudo apt-get update

```

```


sudo apt-get upgrade


```

this will get you up to date.

Or you could click on update manager in >System>Administration>

---

### Post by norwoods on 2009-03-22
what version of ubuntu are you running; ubuntu, kubuntu, xubuntu and 8.04, 8.10, 9.04, etc?
what video hardware do you have; nvidia, ati, etc and version?

---

### Post by Karisma on 2009-03-23
> **norwoods said:**
> what version of ubuntu are you running; ubuntu, kubuntu, xubuntu and 8.04, 8.10, 9.04, etc?
what video hardware do you have; nvidia, ati, etc and version?

I am using Xubuntu 8.10
my video card is VIA CLE266

---

### Post by norwoods on 2009-03-23
info from [http://wiki.archlinux.org/index.php/Via_Unichrome#Unichrome_and_OpenGL](http://wiki.archlinux.org/index.php/Via_Unichrome#Unichrome_and_OpenGL)

Unichrome and OpenGL

OpenGL support for Via's graphic chipsets is seriously outdated. At the moment you will not be able to run more fancy applications, games or compositing desktops like Compiz Fusion that rely on OpenGL as a backend, because the more recent OpenGL extensions are not yet supported in Unichrome 3D driver. You will be able to run simple OpenGL-applications though. The 3D driver for Unichrome is provided by the the DRI project.

Install unichrome-dri, libgl and mesa -packages to get OpenGL to work.

you might want to ask at the via forum site [http://www.tkarena.com/forums/video-graphics-arena/](http://www.tkarena.com/forums/video-graphics-arena/)

---

