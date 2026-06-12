---
title: "graphics card and diver"
date: 2008-11-01
forum: General Help
---

### Post by hndaklr8480 on 2008-11-01
hey ubuntu family i have a quick and probably simple question.  I pretty sure that my computer is running a intel graphics accelerator 950 graphics card and if so i want to make sure that Ubuntu is running the proper drivers so question is how do i check. thanx for any help

---

### Post by nitrousoxide82 on 2008-11-01
Try using [FONT="Lucida Console"]glxinfo | grep "renderer"[/FONT] on the terminal. It will show 3D support info. You should see the string for the Intel DRI driver.

---

### Post by hndaklr8480 on 2008-11-01
OpenGL renderer string: Mesa DRI Intel(R) 945GM 20061017 x86/MMX/SSE2



have an intel gma 950 but review says excellent 3d grafics my starwars game is choppy

---

