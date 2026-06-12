---
title: "Radeon 7500 M. and TV-out"
date: 2005-03-30
forum: Hardware &amp; Laptops
---

### Post by fa2k on 2005-03-30
Hi,

I am about to install Ubuntu, but I would like to know how the multiple monitor- and TV-out support is. I use TV-out frequently and the VGA connector occasionally with Windows, and then I just use Alt-F5, and Fn-F8, respectively, to "clone" the desktop. The video card is a Radeon 7500 Mobility. Can TV-out be done on this card in Ubuntu?

Thanks, 
Marius

---

### Post by fdoving on 2005-03-30
I've done TV-out on older ATI cards a few times.. with atitvout -> [http://www.stud.uni-hamburg.de/users/lennart/projects/atitvout/](http://www.stud.uni-hamburg.de/users/lennart/projects/atitvout/)

Worked without problems. Just remember to connect the S-video cable before booting.. some computers doesn't initialize the s-video port without something connected at boot. At least that was a problem I had on my old Dell Inspiron.

Hope this helps..

---

### Post by panabar on 2005-03-30
I have a laptop with radeon mobility 7500, I can  try tv out tomorrow and tell you about it.

---

### Post by zep24 on 2005-03-30
If you want to use TV-out to watch videos, you will need to set overlay to this and you will probably need to install xvattr. You can find a working deb [here](http://www.dtek.chalmers.se/groups/dvd/deb/)

then to switch overlay type in a terminal

xvattr -a XV_SWITCHCRT -v *"depending on the screen you want to use"*

---

### Post by fa2k on 2005-03-31
[QUOTE=fdoving]I've done TV-out on older ATI cards a few times.. with atitvout -> [http://www.stud.uni-hamburg.de/users/lennart/projects/atitvout/](http://www.stud.uni-hamburg.de/users/lennart/projects/atitvout/)

Worked without problems. Just remember to connect the S-video cable before booting.. some computers doesn't initialize the s-video port without something connected at boot. At least that was a problem I had on my old Dell Inspiron.

Hope this helps..[/QUOTE]


I tried that on Slackware, but I had to make a lot of changes to the xorg configuration. Dit it work for you with just installing and using that program?

---

### Post by panabar on 2005-04-01
I tried Tv and monitor out and only monitor out worked. 
If you boot when monitor is connected you don't get picture on laptop lcd, if you connect monitor while working then you have image on both screens. 

I couldn't manage to enable tv out. I think I have to do some reading.

---

### Post by fa2k on 2005-04-02
Thank you for trying that out :) I have installed Ubuntu now, but I need to get ACPI S3 working before I start to experiment with TV-out. I'll post the solution here if I get it to work ;)

---

