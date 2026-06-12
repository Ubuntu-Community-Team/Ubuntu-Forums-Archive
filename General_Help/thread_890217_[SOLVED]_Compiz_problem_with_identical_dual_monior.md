---
title: "[SOLVED] Compiz problem with identical dual moniors"
date: 2008-08-14
forum: General Help
---

### Post by charonred on 2008-08-14
I using a ASUS ATI Radeon HD2600 Pro card with Ubuntu 8.04.1 on dual 19¨ LCD monitors. I have the restricted drivers installed with Catalyst Control Centre and am running the Compiz window manager.

I had 2 x 19¨ monitors; a Viewsonic VA912 and a Chimei CMV945A and everything worked fine. Last week the Chimei died (gone away for warranty now), so I bought a Samsung SyncMaster 943N.

With the Viewsonic and Samsung things continued to work fine; but I decided that it would be better having 2 identical Samsungs (same gamma, brightness, contrast etc) - that´s where the trouble began.

All´s fine in XP, but when I boot to Ubuntu, the place where the Launcher panel at top is fine on monitor 2, but on monitor 1, it has a black area at top instead of continuation of desktop wallpaper, and it has a trail or ghost of the Launcher panel from monitor 2 (see attachments)

I tried changing the launcher from monitor 2 to 1, but it made no difference to the problem. When I change to KWin window manager and then back to Compiz, the problem is fixed - so any ideas on how to fix this permanently?

---

### Post by charonred on 2008-08-20
still have this problem.

---

### Post by charonred on 2008-08-27
Don't know what happened, but it now starts with wallpaper occupying whole desktop on both monitors (half photo each), but I have to reload Window Manager before Compiz will work correctly (otherwise I have no 'Title Bar' on any windows).

This is starting to look like a re-install of Ubuntu to get it working properly.

---

### Post by charonred on 2008-10-12
seemed to have fixed the 'having to reload windows manager' problem.

Instead of going to Compiz Fusion Icon and getting it to reload WM, I went to system>preferences>appearance clicked the 'Visual Effects' tab and saw it was set to none, I changed it to 'Extra' and closed the window.

Now when PC boots it loads WM correctly and the windows have title bars and Compiz works as it should - seems it forgot it settings ??

---

