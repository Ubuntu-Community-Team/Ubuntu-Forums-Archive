---
title: "video playback problem intel Mobile GM965/GL960"
date: 2008-03-06
forum: Hardware &amp; Laptops
---

### Post by mcs1 on 2008-03-06
For all my sins I have bought a Toshiba laptop with an intel Mobile GM965/GL960 graphics accellerator. I thought I get a graphics card with open source driver to avert problems :(
Anyway, I installed compiz by switching off blacklisting. Now Video was not working anymore so I removed compiz doing:
```
 apt-get --purge remove compiz*
``` 
Tha removed all of the packages ( as far as I can see) but still no video in any of kaffeine, vlc, mplayer
Mplayer gives:
```
 X11 error: BadAlloc (insufficient resources for operation)?,?% 0 0
```
If I use Xwindow without acceleration, totem e.g. works.
Any ideas would be greatly appreciated!

Thank you MCS1

---

### Post by mcs1 on 2008-03-07
Solved my own problem. Good isn't it? :)
If anyone is interested run:


```
 sudo dpkg-reconfigure xserver-xorg 
```
No need to change anything, just worked afterwards????
Cheers

MCS1

---

