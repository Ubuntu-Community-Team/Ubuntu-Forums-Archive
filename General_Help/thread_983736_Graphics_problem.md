---
title: "Graphics problem"
date: 2008-11-16
forum: General Help
---

### Post by benander on 2008-11-16
I recently installed several games and am having an unexpected graphics display problem. Games such as Supertux2 and Neverball load but the graphics do not display correctly.  It might be my laptop since it's cheap but I thought I'd ask around.

I have an Acer Aspire 5315, running Intrepid Ibex.

---

### Post by Marcus Derekus on 2008-11-16
What graphics card do you have?

---

### Post by eternalnewbee on 2008-11-16
> What graphics card do you have?
To check go to: **Main Menu > System > Administration > Hardware Drivers**.

---

### Post by benander on 2008-11-17
nothing in System -> Admin -> Hardware drivers   but I have this graphics card

lspci

00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)

00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)

---

### Post by benander on 2008-11-17
so I've been messing with the games a little and for some reason I can navigate "neverball" with the arrow keys but when I try to load a level the graphics mess up. The ball doesn't load and most textures do not load

---

### Post by Marius Derekus on 2008-11-17
Display the output of this command, **glxinfo | grep direct **

---

