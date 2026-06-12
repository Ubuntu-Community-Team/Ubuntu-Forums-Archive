---
title: "Boot up killed, sometimes"
date: 2008-08-21
forum: General Help
---

### Post by gigaSproule on 2008-08-21
Sometimes Ubuntu doesn't want to start. It goes through the usual dell start up screen followed by the grub countdown and then the nice orange bar to load Ubuntu. Then, sometimes, it stops and goes to a load of command line looking things saying that everything is done, but at the bottom it just says killed. I made a fresh install to see if I had messed up somewhere before, but it seems to have done the same thing again. I have a feeling it has something to do with my graphics card driver (EnvyNG ATi install). Are there any known issues with it or any reason why it is happening?

---

### Post by zensor on 2008-10-29
> **gigaSproule said:**
> Sometimes Ubuntu doesn't want to start.[...] it just says killed.

Hmm, the same happens at my Laptop
Usually it happens after powernowd; today it happened after winbind (I installed wine yesterday... so maybe there is a connection?)

Now maybe a little help:
STRG+ALT+F2 opens a console and lets me login
"startx" even opens the graphic interface
But then a HAL-error occurs.

I can do some things, others (WLAN) do not work and shutting down is not possible: clicking the shutdown-button opens the normal dialoge (after about a minute) and then there is no button for shutting down, just 3 of 7 Buttons are there - I think the first line Switch User; Lock Screen; Log out - but not the rest shut down; hibernate; stand by, reboot
Pressing the hardware-On-Button for ten seconds of course helps :-)

I hope that helps you a little and that there is someone, who can help both of us a lot ;-)

zensor

---

