---
title: "low fps"
date: 2005-05-30
forum: Hardware &amp; Laptops
---

### Post by Dave88 on 2005-05-30
I have ati radeon 9200 which is set up using this [http://www.ubuntuforums.org/showthread.php?t=24557&highlight=ati+radeon](http://www.ubuntuforums.org/showthread.php?t=24557&highlight=ati+radeon) tutorial and everything seems fine...
```
dave@ubuntu:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9200 DDR Generic
OpenGL version string: 1.3.4769 (X4.3.0-8.8.25)

dave@ubuntu:~$

```

but the fps doesn't seem too good from
glxgears
```
dave@ubuntu:~$ glxgears
2855 frames in 5.0 seconds = 571.000 FPS
3760 frames in 5.0 seconds = 752.000 FPS
3760 frames in 5.0 seconds = 752.000 FPS
3760 frames in 5.0 seconds = 752.000 FPS
3761 frames in 5.0 seconds = 752.200 FPS
3759 frames in 5.0 seconds = 751.800 FPS
dave@ubuntu:~$

```
Anyone know how to get a higher fps with this card (ati radeon 9200)??

thanks.

---

### Post by graigsmith on 2005-05-31
im using the open source drivers.  that came with ubuntu.  the open source drivers are capable of 3d up to the 9200.  if you have anything higher than that, the open source drivers dont work.   im getting this on my 9200 with the open source drivers in glxgears.

7686 frames in 5.0 seconds = 1537.200 FPS
7714 frames in 5.0 seconds = 1542.800 FPS
7645 frames in 5.0 seconds = 1529.000 FPS

Also i hear that glxgears is not really a performance measurement tool, and you should see how well games play.   What games have you tried?  have you tried enemy territory?  i am able to play it quite well at 800x600 on my 9200.

---

### Post by Dave88 on 2005-05-31
I havn't tried games yet, anything i can get from apt-get or some free *.deb packages to test the card?

thanks

---

### Post by teevee on 2005-05-31
[QUOTE=Dave88]I havn't tried games yet, anything i can get from apt-get or some free *.deb packages to test the card?

thanks[/QUOTE]
Tux Racer, it's in universe.

---

### Post by Dave88 on 2005-05-31
thanks, that worked pretty smooth!

Good game too.

---

### Post by penvzila on 2005-05-31
I have a laptop with an 128mb 9700 pro, and the ATI linux drivers are pretty much crap.  I get around 2000 in glxgears.

My desktop, with half the processing speed, RAM, and a "slower" video card rapes my laptop (in linux, anyway).  It's because NVIDIA actually cares about it's linux drivers.

---

### Post by Dave88 on 2005-05-31
Well next time I buy a graphics card I know it will be an nvida!!

---

