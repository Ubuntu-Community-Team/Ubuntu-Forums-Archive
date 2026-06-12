---
title: "ATI X1200 series crappy Performance (X1270)"
date: 2009-05-19
forum: Hardware
---

### Post by sdm_cacto on 2009-05-19
Hi, Im using Ubuntu Jaunty on a Dell Inspiron 1525 laptop, wich has an ATI Radeon x1270 integrated videocard.
 It seems to work fine, except when I try to run any 3D game, its just super slow. Videos play great, even using gnome compositing, Compiz Fusion runs pretty slow, but acceptable (I'd say 10~15 FPS, while using FLGRX in Ubuntu Intrepid was very smooth) and when I try GLXGEARS i get less than 300 fps (wich is VERY low)

any ideas?xorg tweaks I can try? experiences?
I know its a very low end card but it should at least run Neverball smoothly

> 
01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]


---

### Post by toughengineer on 2010-05-20
> **sdm_cacto said:**
> Hi, Im using Ubuntu Jaunty on a Dell Inspiron 1525 laptop, wich has an ATI Radeon x1270 integrated videocard.
 It seems to work fine, except when I try to run any 3D game, its just super slow. Videos play great, even using gnome compositing, Compiz Fusion runs pretty slow, but acceptable (I'd say 10~15 FPS, while using FLGRX in Ubuntu Intrepid was very smooth) and when I try GLXGEARS i get less than 300 fps (wich is VERY low)

any ideas?xorg tweaks I can try? experiences?
I know its a very low end card but it should at least run Neverball smoothly
i have the same problem but with ATI Radeon X1200 Series 

anyone can help ?!

---

### Post by sdm_cacto on 2010-05-20
What happenes is that your card (and mine) is not supported anymore by ATI, but they opened part of the driver's code so now we use an open source driver, called RADEON wich is mantained by the community. While it works pretty well it's no good for playing 3D games (the video card is really slow by itself).

My advice: turn off compiz, use desktop compositing (or not) and stay away for 3D games.

---

### Post by toughengineer on 2010-05-24
thnx for the advice ;)
good solution .. but i still search for a way to install my ati driver .. i got it from AMD but i can't install it 
this missage shows to me 

Error: ./default_policy.sh does not support version
default:v2:i686:lib::none:2.6.32-22-generic; make sure that the version is being
correctly set by --iscurrentdistro

u know anything about that ?!

---

### Post by sdm_cacto on 2010-05-24
Yes,as I wrote above, the official driver (fglrx) is not supported for your card anymore, so you have to use either a really older version of ubuntu (8.04-8.10) or the open source dirver (RADEON) wich is what you use by default

---

### Post by Tomi Neste on 2010-05-25
The problem is that my x1200 used to be very slow but somewhat usable with the OSS drivers in 9.10 but after upgrading even that performance is completely gone. What happened?

I know that x1200 is not a powerhouse but it works very smoothly with Vista.

---

