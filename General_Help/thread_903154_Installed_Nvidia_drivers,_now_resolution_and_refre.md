---
title: "Installed Nvidia drivers, now resolution and refresh rate is messed up - Please help"
date: 2008-08-28
forum: General Help
---

### Post by Timberwolf5578 on 2008-08-28
I installed nvidia drivers for my graphics card with envyng but now my screen resolution is too widened and my refresh rate is too low.  How can I fix this?

---

### Post by Crafty Kisses on 2008-08-28
Take a look at this > [http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)

---

### Post by Timberwolf5578 on 2008-08-28
> **Codename said:**
> Take a look at this > [http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)

That is way too complex.  All I want to do is have my resolution at 1024x768 and 100mhz refresh rate.  There has to be an easier way to do that.

---

### Post by Rhubarb on 2008-08-28
Run this:
```
gksu displayconfig-gtk
```
Select your Screen model and resolution.
If you can't choose your refresh rate, don't worry, because this can be added to your /etc/X11/xorg.conf file later (do a search for "refresh rate nvidia xorg.conf")
Then log out, log back in again.

---

