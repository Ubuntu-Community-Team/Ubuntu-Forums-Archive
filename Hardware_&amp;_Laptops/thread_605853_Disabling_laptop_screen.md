---
title: "Disabling laptop screen"
date: 2007-11-07
forum: Hardware &amp; Laptops
---

### Post by neemz on 2007-11-07
Hi folks

When I work from home I put my laptop on a shelf, plug it in and turn it on. It then boots to the GDM login screen.

I then load up freeNX on my main PC and log in to it fullscreen. This is because I don't have the space for both my main PC and my work laptop on my desk.

What I would like to be able to do though is to turn the laptops screen off, currently when i try and close the laptops lid by freenx session blanks out but the laptops display stays illuminated at the GDM login prompt. If I move the mouse on my main PC I then have to type my password in to unlock the session.

What I would like to happen is as follows. 
I would like the laptop screen to shut off so that it is safe to keep it closed without it effecting my remote session.

I don't mind if I have to do something like tab into a virtual screen and kill GDM and type a command to blank the screen, aslong as the screen is off and no longer generating heat.

Many thanks
Jon.

---

### Post by elamericano on 2007-11-07
xrandr --output LVDS --off

This works for me, but I have the Radeon driver. Your driver may not support it yet.

---

