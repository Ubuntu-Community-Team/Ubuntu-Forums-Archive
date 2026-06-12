---
title: "Screen wont go to sleep while I'm logged in."
date: 2008-07-27
forum: General Help
---

### Post by mobilediesel on 2008-07-27
I have my desktop running Xubuntu 8.04.1. I have it set to run the screensaver after 9 minutes, then put the display to sleep after 10 minutes. The screen never goes to sleep. I discovered that the screen WILL go to sleep when inactive if it's sitting at the login screen and I haven't logged in yet. Once I log in, the screensaver will activate when I want, but the monitor will not shut down.

I've looked all over the forum via google and can't find a solution. I've only found people pointing to "Applications->Settings->Settings Manager->Screen Saver->Power Management."
That doesn't help because it IS set to put the display to sleep, it just wont do it.

---

### Post by jimmy the saint on 2008-07-27
the solution is here:  [http://ubuntuforums.org/showthread.php?t=854557](http://ubuntuforums.org/showthread.php?t=854557)

It is an issue with the gnome-screensaver not autostarting.  just follow the thread power settings should start to work.

---

### Post by mobilediesel on 2008-07-27
> **jimmy the saint said:**
> the solution is here:  [http://ubuntuforums.org/showthread.php?t=854557](http://ubuntuforums.org/showthread.php?t=854557)

It is an issue with the gnome-screensaver not autostarting.  just follow the thread power settings should start to work.

I was already able to get to power management through the screen saver settings under Applications->Settings->Settings Manager.
I already have it set to put the display to sleep after 10 minutes but it just doesn't put the display to sleep if I'm logged in. If I start the computer and don't log in right away, the screen goes to sleep after 10 mintes.
> **mobilediesel said:**
> it IS set to put the display to sleep, it just wont do it.

---

### Post by jimmy the saint on 2008-07-28
You need to enable the gnome-screensaver package for any of the power management options to take effect.  It doesn't matter what you tell it to do through the power management options unless you do this.  The setting do absolutely nothing until you set gnome-screensaver to run at startup manually.

---

