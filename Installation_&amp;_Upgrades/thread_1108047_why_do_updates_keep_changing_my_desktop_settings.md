---
title: "why do updates keep changing my desktop settings?"
date: 2009-03-27
forum: Installation &amp; Upgrades
---

### Post by asynchronous13 on 2009-03-27
After a recent update this week, I could no longer add or remove icons from the gnome panel at the top of the screen. right-click -> Add to Panel .... but nothing would happen. Finally got that sorted out.

Now today, post-update my workspace switcher reduced to only 2 desktops (simple to fix - but why was it changed?). Several keyboard shortcuts are gone, and the all the Compiz eye candy is no longer working (the settings are enabled, but no love). 

No time at the moment to fix it, as I actually need to do some work. But any suggestions would be appreciated.

---

### Post by bapoumba on 2009-03-27
Which version of ubuntu are you running ?

---

### Post by asynchronous13 on 2009-03-30
Ubuntu 8.10, Intrepid Ibex

---

### Post by bapoumba on 2009-03-30
```
killall gnome-panel
```
?
Is it the same after a reboot?

---

### Post by benjaminjames on 2009-03-30
have you connected a second display or linked it up to your tv?? because my eye candy stopped when i hooked up my plasma.

---

### Post by asynchronous13 on 2009-03-31
> **bapoumba said:**
> 
Is it the same after a reboot?

Yes, I've rebooted a couple times just to make sure. I finally made some time to figure this out today. I had to re-install the nvidia graphics driver -- now things seem to be back to normal.

Is there a way to automate this process?

---

