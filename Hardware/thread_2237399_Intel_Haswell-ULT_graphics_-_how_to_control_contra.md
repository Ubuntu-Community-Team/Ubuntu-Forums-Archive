---
title: "Intel Haswell-ULT graphics - how to control contrast and saturation?"
date: 2014-08-01
forum: Hardware
---

### Post by sgofferj on 2014-08-01
Hi,

I'm trying to get a nicer picture on my new Acer E1-572 laptop with kubuntu 14.04 but the only thing I can control so far is display brightness. Is there a way to control contrast and saturation/vibrance/gamma? The screen looks pretty washed out, compared to my desktop (NVidia GTX 770 + Samsung T27C370).

-Stefan

---

### Post by Vladlenin5000 on 2014-08-01
Nvidia settings, perhaps?

---

### Post by ajgreeny on 2014-08-01
Look at **xgamma** to change that setting, but I can't help with brightness or contrast if the gamma setting does not work.
```
xgamma -gamma 0.5
``` should reduce gamma for all RGB though you can set each separately if you need to.  Just try different figures at the end. I forget what the upper/lower limits are but I'm sure a search will find them for you.

---

### Post by sgofferj on 2014-08-01
> **Vladlenin5000 said:**
> Nvidia settings, perhaps?
I doubt, nvidia-settings can control Intel Haswell-ULT graphics ^^

@ajgreeny:
I'll check that, thx.

---

