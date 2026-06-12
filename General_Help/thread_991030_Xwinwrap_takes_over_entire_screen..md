---
title: "Xwinwrap takes over entire screen."
date: 2008-11-23
forum: General Help
---

### Post by vespar on 2008-11-23
Just recently switched over to Linux and definitely enjoying it so far.

Anyhow, I got Compiz Fusion and all that finally working but the icing on the cake was going to be getting xwinwrap to work along with it. Whenever I try making it use the default glmatrix screensaver command:
xwinwrap -ni -argb -fs -s -st -sp -b -nf -- /usr/lib/xscreensaver/glmatrix -window-id WID -delay 50000 -no-fog -density 40

My screen suddenly acts as if it is in screensaver mode. The screensaver will play over my entire desktop and the desktop only becomes available when I move the mouse around and that only last for under a second. (Basically as if it is trying to go into screensaver mode 24/7 and fights for control over me being active).

Any idea why this is? I was under the assumption the -b command would make it run in the background?

---

### Post by easybake on 2008-11-23
> **vespar said:**
> 
xwinwrap -ni -argb -fs -s -st -sp -b -nf -- /usr/lib/xscreensaver/glmatrix -window-id WID -delay 50000 -no-fog -density 40
Any idea why this is? I was under the assumption the -b command would make it run in the background?

The -b control really means below.

One of the easiest ways to change the appearence of the effect is to adjust the opacity of the effect by adding -o 0.2 (you can change the 0.2 to anything between 0 and 1)

If you want another cool thing to do with xwinwrap you can check my tutorial. [Here]("http://ubuntuforums.org/showthread.php?t=883176")

---

