---
title: "Compiz works too slow"
date: 2008-07-11
forum: General Help
---

### Post by DexterLB on 2008-07-11
Since I have a custom kernel, compiz works a bit slow (animations and seffects work fine), but when I click to open a context menu or a combo box, It appears after one second, not instantly. And the wierd thing is that on my TV (seperate X screen) all menus and combo boxes work fine! Is it something in the X configuration? (in CCSM everything is the same for both screens)

P. S. This is not affected by the CPU! no matter how many processes and how much free CPU time I have, the dalay between clicking and appearing is always around a second! And I tried to disable all effects and plugins and it also doesn't work!

---

### Post by sayakb on 2008-07-11
Open CCSM, Click Preferences and click Restore to Defaults. If you GPU doesn't support plugins like Blur and Bicubic, don't enable them.

---

### Post by DexterLB on 2008-07-11
I tried that several times. No effect

---

### Post by sayakb on 2008-07-11
Which graphics card do you have?

---

### Post by DexterLB on 2008-07-12
--------UPDATE--------
I fixed it! (Guess what! mistake in xorg.conf!) I reconfigured xserver-xorg, restarted X and configured my NVIDIA to use my TV as a second X screen (by reconfiguring xorg that was wiped out) and now compiz works fine.

P. S. How do I mark the thread as solved?

---

