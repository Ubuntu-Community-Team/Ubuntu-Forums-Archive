---
title: "Ubuntu 9.10 Problems"
date: 2009-10-31
forum: Installation &amp; Upgrades
---

### Post by 59chip on 2009-10-31
Just upgraded to 9.10, big problems.  4 out of 5 times the desktop hangs to a black screen with blinking cursor in top left corner.  When it does work it is extremely slow.  Process called compiz real uses 100% CPU.  Please help!

---

### Post by lemming465 on 2009-11-01
You don't mention your video chip, but it appears that your X server support has regressed.  There is a lot of churn in the X codebase at present, and that will probably continue for another two years, so this sort of thing is going to bite people occasionally.  If you get a working boot, go into System->Preference->Appearances, visual effects tab (right-most), and select the "none" radio button, then reboot.  That should turn off the compiz stuff, which ought to fix your CPU problem and might also fix your stability problem.

---

