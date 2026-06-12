---
title: "Fixed &quot;Unable to open KSplashX&quot; (KDE4.1)"
date: 2008-08-23
forum: General Help
---

### Post by clay_in_nj on 2008-08-23
I wanted to try out a couple of new splash screens, but even on the "Test Theme" button in System Settings, I would just get this error message "Unable to open KSplashX" and when restarting, the splash would just not show up at all. After a little research online, I found that it probably would entail moving the splash files, but the reference I found was for a different distro. Well I found it. If you have this same problem, try:

sudo mv ~/.kde4/share/apps/ksplash/Themes/*THEMEDIR* /usr/lib/kde4/share/kde4/apps/ksplash/Themes/

(replace *THEMEDIR* with the directory name for your theme.)

Now, start System Settings, and you new theme should work.

---

### Post by JackieBrown on 2008-12-17
You might have a typo (or it might just be different in Debian) but the system path on my machine was /usr/share/kde4/apps/ksplash/Themes

---

