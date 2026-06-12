---
title: "screen shell"
date: 2008-07-18
forum: General Help
---

### Post by xoger on 2008-07-18
is it possible to change the screen orientation in a shell file

---

### Post by haegl on 2008-07-18
Change the orientation of the console or a file [like an image]?

---

### Post by xoger on 2008-07-18
the whole screen

---

### Post by haegl on 2008-07-18
I've never tried it... however there is an interesting post about it :
[http://osdir.com/ml/distributions.gr.../msg00112.html]("http://osdir.com/ml/distributions.grml.user/2006-11/msg00112.html")

[Link fixed]

---

### Post by xoger on 2008-07-18
404: page not found

---

### Post by chrisccoulson on 2008-07-18
You might find the following useful for manipulating your display from a script:

[http://www.thinkwiki.org/wiki/Xorg_RandR_1.2]("http://www.thinkwiki.org/wiki/Xorg_RandR_1.2")

And also:
```
man xrandr
```

---

### Post by Rhubarb on 2008-07-18
xrandr doesn't seem to be able to rotate / invert with my nvidia card.
It looks like (if you are running the nvidia proprietary drivers) you should be able to achieve this with nvidia-xconfig:
[http://linux.die.net/man/1/nvidia-xconfig](http://linux.die.net/man/1/nvidia-xconfig)

---

### Post by chrisccoulson on 2008-07-18
If you want to be able to rotate your screen using xrandr and the NVIDIA proprietary drivers, you need to add the following line to the Device section of your /etc/X11/xorg.conf:
```
Option "RandRRotation" "True"
```

---

### Post by Rhubarb on 2008-07-18
> **chrisccoulson said:**
> If you want to be able to rotate your screen using xrandr and the NVIDIA proprietary drivers, you need to add the following line to the Device section of your /etc/X11/xorg.conf:
```
Option "RandRRotation" "True"
```
Thanks for the info there chrisccoulson, but I've found it doesn't work in the Device section, it only works for me in the Screen section of my xorg.conf

---

