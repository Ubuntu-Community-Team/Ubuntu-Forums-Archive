---
title: "Intel screen tearing"
date: 2008-03-08
forum: Hardware &amp; Laptops
---

### Post by natesully on 2008-03-08
Well, I read some older threads about this already.  Is there any actual solution for tearing in EVERYTHING (zsnes, compiz, video, you name it- it doesn't work right) on Intel grahpics chipsets?

I tried (and failed) compiling the latest driver from git repositories, and ended up with 2D only.  I could not figure out the overlay patch on the xorg mailing list, it will not go on the latest drivers.  I had Gentoo a week ago, so I don't think the latest anything will fix this.  And XP works fine, so it is a silly software problem somewhere.

Anyone have a working Intel video setup?  This is on a Dell Vostro 1400, with a G965M or something like that.

---

### Post by natesully on 2008-03-08
After some messing around with various settings, such as DriConf and Compiz's refresh rate, I somehow got ZSNES to sync while compiz kept tearing, like normal.  While trying to figure out how I did that, I somehow made it worse- now my custom-built ZSNES crashes when using OpenGL mode, and the zsnes32 works fine, but neither sync.  I really have no clue how I did that.  There is seriously something wrong with either the intel video driver, or xorg.

Does anyone know how to compile the latest xorg, intel driver, mesa, etc. on Ubuntu?  Perhaps using the freshest versions possible will help.

---

### Post by natesully on 2008-03-10
Well, I'm trying everything in my power to compile xorg from git, but it is not working.  Building X is rediculously complicated these days, it's a wonder Gentoo ever worked right.  Built drivers and GL apps will not run at all, but I do have xorg working.  For some insane reason, zsnes still runs with OpenGL on (but crashes and takes X with it when you exit).  And it tears still.

I give up.  There must be no solution to this (besides "Windows XP").

---

