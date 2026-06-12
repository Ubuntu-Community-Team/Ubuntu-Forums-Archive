---
title: "Nvidia not showing second card"
date: 2011-02-07
forum: Hardware
---

### Post by mwszalek on 2011-02-07
I've got two GTX 480 cards installed on my system, when I do a lspci they are both there, but the nvidia settings only show one device. 

I'm running 32bit 10.10, and it needs to stay that way. I did notice that when I installed 64bit 10.10, it detected both cards just fine. Unfortunately because of some other software restrictions I need to run 32bit.

Has anyone seen this issue? Doing several hours of searching turned up one possible lead. adding vmalloc=196M to my boot parameters, but while I'm not entirely new to linux in general, I am new to Ubuntu 10.10 and I can't seem to figure out how to change boot parameters, so maybe a little help with that?

---

### Post by mwszalek on 2011-02-07
Ok so this may be helpful to other folks so I'll post my fix for this:


The hint I got earlier about adding vmalloc=196M to my boot parameters was on the right track. Turns out it started working once I changed it to 256M.


I used the instructions I found here:

[http://ubuntuforums.org/showthread.php?t=1571606&page=4](http://ubuntuforums.org/showthread.php?t=1571606&page=4)

---

