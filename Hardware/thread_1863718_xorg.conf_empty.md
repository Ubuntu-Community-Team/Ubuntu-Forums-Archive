---
title: "xorg.conf empty?"
date: 2011-10-18
forum: Hardware
---

### Post by Jay105 on 2011-10-18
hi  

after having a few problems with various things after a kernel upgrade on my fedora partition, i have been pointed in the direction of my xorg.conf file in order to fix my graohics card problems and my mouse (while being recongized) not moving around the screen problems. 

i tried ```
sudo gedit /etc/modprobe.d/xorg.conf
``` only to find it blank. i also tried ```
sudo gedit /etc/x11/xorg.conf
``` and found only the same thing. surely this is the root and cause of all my problems. how do i fix this?:confused:

---

### Post by 23dornot23d on 2011-10-18
What graphics card do you have please ?
(the following command in a terminal may hel if you do not know) LSPCI in lower case

lspci

and what version of Ubuntu do you run ? or is it just Fedora we are dealing with here
in which case what version of Fedora ?

---

### Post by Leaf on 2011-10-18
it's /etc/X11/xorg.conf
not x11

Case sensitive!

---

### Post by dasan on 2011-10-18
Leaf you are true...
But I think it is pretty normal coz I have noticed it many times...

if you enter it properly it will work very fine...

In my case I can work with default settings and blank xorg.conf 
but when i enable nvidia driver and  write to it i can set better resolution and get better graphic effects....

---

