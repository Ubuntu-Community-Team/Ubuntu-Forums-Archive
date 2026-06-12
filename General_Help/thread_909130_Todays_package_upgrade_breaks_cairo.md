---
title: "Todays package upgrade breaks cairo?"
date: 2008-09-03
forum: General Help
---

### Post by bevis on 2008-09-03
Today I upgraded a few packages as requested by the 'upgrade notification' icon on the desktop, and now after a reboot, gnome will not start.

Running 'gnome-session' stops with:

**symbol lookup error: /usr/lib/libcairo.so.2: undefined symbol: FT_Library_SetLcdFilter**

for a host of apps.  After running twm, I find that most X apps are failing to start up with the same error now.

What has been released in todays update which might have broken this, and how might I fix it? (given I only have command line / twm access!)

I'm running ubuntu 8.  Libcairo.so.2 is libcairo.so.2.17.3.

---

### Post by bevis on 2008-09-03
Well, manually installing a newer cairo (1.6.4 over 1.6.0) fixed most of the problems, but some things are still not quite right, like some of the fonts being used.

---

