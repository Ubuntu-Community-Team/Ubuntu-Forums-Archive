---
title: "Transmission No Longer In Tray"
date: 2008-11-09
forum: General Help
---

### Post by Jerrac on 2008-11-09
Since I upgraded to 8.10, Transmission doesn't minimize to the tray anymore. Why is that? And is there a way for me to make it minimize to the tray? I checked the all the preferences for a setting to change and couldn't find anything.

Thanks!

Ah! Figured it out. Open the /home/"user"/.config/transmission/settings.json file and set the "show-tray-icon": 0, to "show-tray-icon": 1,. 

Though I don't get why there isn't a gui option for that... 

Hopefully this will help someone else instead of displaying my stupidity in not checking the actual config files first....

---

### Post by adult swim on 2008-11-09
if you go to the view menu, there is a box for the tray icon

---

### Post by Jerrac on 2008-11-09
> **adult swim said:**
> if you go to the view menu, there is a box for the tray icon

Oh. *bangs head on desk*

---

### Post by sanchdaniel on 2009-03-09
**slams head on desk**

---

### Post by Jerrac on 2009-03-09
> **sanchdaniel said:**
> **slams head on desk**

Glad I'm not the only one.

Just found that the version in Jaunty has that option listed in Preferences->Desktop. For future referencce... :D

---

### Post by maligent on 2009-03-10
Ouch, ... that's all I got

---

### Post by musicguyguy on 2009-05-08
well, all that head-->table business has gotten me the answer i needed! thanks!

---

### Post by Agilar on 2011-08-09
Yeah - in Natty (11.04) it's now at

Prefences -> Desktop -> Show transmission icon in notification area;

And clicking the notification icon minimizes transmission to the system tray.

---

