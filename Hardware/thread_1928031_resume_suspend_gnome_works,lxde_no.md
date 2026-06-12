---
title: "resume suspend gnome works,lxde no"
date: 2012-02-19
forum: Hardware
---

### Post by maestrobwh1 on 2012-02-19
Ubuntu Lucid.  I have been using an OQO model 02 for a while and like gnome but find the processor is most relaxed with LXDE (installed lubuntu-desktop) but I can only resume properly once from LXDE.  Gnome is seemingly infinite. The second resume running LXDE results in the backlight coming up, but no screen.  crtl alt F4 doesn't drop me to a shell where I can just restart gdm (kept it as display manager).  I have to do a hard reset w power button.

KDM has a TerminateServer=true line which frequently has fixed such issues for me in the past.  

In GDM i have AlwaysRestartServer=true which I think does the same thing because without it, I can't resume Gnome either.

Ideas other than "just use gnome then."  :D

I can logout of LXDE then into gnome, then suspend or use ususwap but both are inconvenient for several reasons.

---

