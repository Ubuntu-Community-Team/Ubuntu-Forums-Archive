---
title: "Direct rendering with 945gm"
date: 2008-06-06
forum: Hardware
---

### Post by mrmogi on 2008-06-06
Hi!

I have a Lenovo 3000 n100 laptop with intel 945gma. I'm running hardy, but the problems discussed were present on gutsy too.

Desktop effects work fine but i have problems with google earth. It works painfully slow. 

Glx info gives me:
gorazd@lenovo:~$ glxinfo | grep direct
direct rendering: No (LIBGL_ALWAYS_INDIRECT set)

But sudo glxinfo:
gorazd@lenovo:~$ sudo glxinfo | grep direct
direct rendering: Yes

gorazd@lenovo:~$ glxgears
4217 frames in 5.0 seconds = 841.195 FPS
4220 frames in 5.0 seconds = 841.728 FPS

I did a fresh install and everything (except DRI) worked fine. Then I tried different drivers (i810, intel experimentall modesetting driver) in hope to get DRI working, but had many problems just to get the right resolution. At the moment the Screens and graphics says driver:none.

Any ideas?

---

