---
title: "[SOLVED] Video card control panel, maybe?"
date: 2008-09-22
forum: General Help
---

### Post by mjpatey on 2008-09-22
Hi, group-

I'm in the process of calibrating my monitor for photographic purposes, and have hit a stumbling block early in the process.  My monitor (a Dell 1801FP) gives me control over brightness, but for some reason, not contrast!  The OSD actually has an entry for contrast, but it's greyed out.  A few other parameters are similarly greyed out, but none as important to me as contrast.

So I'm hoping to be able to control these parameters via software.  In particular, I have an nVidia GeForce 6200 AGP with 128 MB video RAM.  I believe the card comes with a Windows control panel applet that would be perfect for this!  But I'm not running Windows.

Is there anything available in Ubuntu that would allow me to control brightness, contrast, gamma, color temp, etc. via software?

Thanks for any ideas you may have!

-Mark

---

### Post by mjpatey on 2008-09-22
Solved!

```
sudo apt-get install nvidia-settings
```

...has all I need!  Google is my friend... I hope this helps someone.  :-)

---

### Post by Bucky Ball on 2008-09-22
> **mjpatey said:**
> Solved!

```
sudo apt-get install nvidia-settings
```...has all I need!  Google is my friend... I hope this helps someone.  :-)

You got it and beat me to saying that! Well done.

Don't forget to mark your thread as solved from Thread Tools and post again with any further ](*,)

---

