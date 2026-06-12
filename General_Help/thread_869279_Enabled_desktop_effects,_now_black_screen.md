---
title: "Enabled desktop effects, now black screen"
date: 2008-07-24
forum: General Help
---

### Post by unknownsoldierX on 2008-07-24
I installed Kubuntu 8.04.1 with KDE4.  When I enabled desktop effects the screen went black.  I rebooted and when I log in the screen is black.

I switch the session to failsafe but all I get is a terminal window.  This is lame and has me worried that things are only going to get worse and harder to use.

How do I get to a failsafe GUI, like in standard Ubuntu?

---

### Post by kuja on 2008-07-28
What instructions did you follow to enable "desktop effects"? One of the changes is probably where the problem lies.

---

### Post by Tim_Olaguna on 2008-07-28
I had a similar problem.  I resolved it (if I remember correctly) by right clicking, selecting "Desktop Effects" (or something like it), then selecting a much lighter Oxygen theme.  I believe I chose the lightest grey theme they offered.  The theme is evidently so transparent it is essentially invisible. Then later I changed to a light brown desktop background picture.  Things are much better now.

---

### Post by unknownsoldierX on 2008-07-28
> **kuja said:**
> What instructions did you follow to enable "desktop effects"? One of the changes is probably where the problem lies.

System Settings > Desktop > Desktop Effects

All I did was put a check in the "Enable desktop effects" box.

---

### Post by kuja on 2008-07-28
My best assumption is maybe your video card/video drivers don't like opengl? Try it over again after backing up and removing  your "~/.kde4" folder and next time you do it, go to advanced options and set it to use xrender instead of opengl.

---

### Post by unknownsoldierX on 2008-07-28
> **kuja said:**
> My best assumption is maybe your video card/video drivers don't like opengl? Try it over again after backing up and removing  your "~/.kde4" folder and next time you do it, go to advanced options and set it to use xrender instead of opengl.

That worked.  However, I don't notice any difference in the appearance of the dektop.

---

