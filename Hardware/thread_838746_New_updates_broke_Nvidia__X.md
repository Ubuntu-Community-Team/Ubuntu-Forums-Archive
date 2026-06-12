---
title: "New updates broke Nvidia / X"
date: 2008-06-23
forum: Hardware
---

### Post by Z_o-s-o on 2008-06-23
I installed some new updates this morning...rebooted...and now Nvidia is broken and Ubuntu cant detect my displays , and insists on running in low graphics mode.

If I go back to the last kernel it works fine, but the -19 no longer works....

---

### Post by sdennie on 2008-06-23
Did you install the nvidia drivers by downloading them from the nvidia website?  If so, you will have to reinstall them.  To prevent having to do that in the future, see: [http://ubuntuforums.org/showthread.php?t=835573](http://ubuntuforums.org/showthread.php?t=835573)

---

### Post by Hashi on 2008-06-23
Hi,
  I have a (I think) similar problem with a similar computer (COMPAQ DV6000 - about 2 years old). I have been running Ubuntu on it since new, so I guess 7.04? Everything was fine.
  Now, with this most recent update, I can only boot into text mode. I have no idea how to fix it, I'm sorry to say, and for me, reverting to a previous kernel didn't help. I may have to re-install, but I will go back to 7.10, it worked fine for me.
Jon

---

### Post by liquidcable on 2008-06-23
Using the package manager reinstall anything that begins with "linux-restricted-modules" and "nvidia" but only reinstall what you already have installed.

You also may have to modify /etc/X11/xorg.conf, but most likely not.

---

### Post by Z_o-s-o on 2008-06-24
Its using the driver from the restricted driver manager...

If I roll back to the -18 kernel, it runs just fine, but for whatever reason, updates (a kernel patch, I believe) broke -19.

---

