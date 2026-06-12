---
title: "problems with compiz 8.10"
date: 2008-11-15
forum: General Help
---

### Post by Wartender on 2008-11-15
i recently installed 8.10 as a dual-boot with vista on my mother's laptop, and i was messing around with compiz's settings with compizconfig-settings-manager and i tried to turn on the magnifier. i had the negative on, which uses super+m as a shortcut key, and magnifier also uses super+m, so it tells me there's a conflict, knowing the reason why i decided to click ignore conflict, and now i can't log in because the screen get all purple and it goes back to the log in screen, i can only log in using the terminal mode, not even safe gnome works. can i fix this or do i have to reinstall ubuntu?

---

### Post by Wartender on 2008-11-16
can somebody help me please? hello?

---

### Post by drs305 on 2008-11-16
Before uninstalling ubuntu I would first try uninstalling compiz. Since you can access the terminal, run the following to get rid of compiz and its settings:
```
sudo apt-get purge compiz
```
If your system starts working again you can always reinstall compiz and not repeat your decision to ignore the conflict.

---

### Post by drown on 2008-12-24
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/292372](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/292372)

Looks like the bug is documented there, but with no solution.

I experienced this problem, logged in using the failsafe terminal (it's under options at the login screen).  From the terminal you can launch the gnome-panel, go into settings>  preferences> sessions, go to 'window manager' in the 'startup programs' tab, choose edit and change the command to 'metacity'.  This should stop compiz from running at next login.

Whilst I was at it I uninstalled emerald (sudo apt-get remove emerald) and compiz (sudo apt-get remove compiz-core), but I'm pretty sure it was switching to metacity that prompted the return of my desktop when I restarted.

---

### Post by beaubeau on 2009-01-01
drown you are wonderful!  Man, i thought i was in trouble there for a moment.  I have a NC10 samsung netbook and your suggestion of going into the window manager and changing to metacity did just the trick!  For some reason the remove compiz from the terminal had not had the desired effect.  
I really appreciate the advice and wanted to take the simple moment to say so.

---

