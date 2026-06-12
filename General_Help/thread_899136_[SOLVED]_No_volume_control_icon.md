---
title: "[SOLVED] No volume control icon"
date: 2008-08-24
forum: General Help
---

### Post by blah5754745 on 2008-08-24
in the upper right corner of screen

I lost it trying the get the creative drivers to work

can somebody help me get it back, my onboard sound works atm just that little icon isn't up there.

see picture:

---

### Post by BenAshton24 on 2008-08-24
Hey!

It seems that you have accidentally removed the volume manager from the task bar. It is really easy to resolve, all you need to do is right click anywhere on the task bar and click "add to panel" then scroll down the list of applets until you see "volume control", double click on it and it should be added to your task bar. If this fails simply run the following command from terminal:
> /usr/lib/gnome-volume-manager/gnome-volume-manager --sm-disable
Hope this helps :D

---

### Post by blah5754745 on 2008-08-24
ur awesome thanks

---

### Post by tux_zEro on 2009-01-23
> **BenAshton24 said:**
> all you need to do is right click anywhere on the task bar and click "add to panel" then scroll down the list of applets until you see "volume control", double click on it and it should be added to your task bar.

Hope this helps :D

Couldn't have thought it would be that simple. This FIXED it. :KS

Actually JRE install last night did something to the sound, so I reloaded all sound packages and in doing so didn't reload Volume control. It was gone on the next boot.

---

