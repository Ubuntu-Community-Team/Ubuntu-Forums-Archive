---
title: "Suspend Password"
date: 2008-07-17
forum: General Help
---

### Post by diilbert on 2008-07-17
I want to remove the password that appears when I resume from suspend.  I know I have done this before (Gusty Gibson), but cannot remember for the life of me how I did it.

Thanks for any ideas !

diilbert

---

### Post by danwood76 on 2008-07-17
This can be set using the gconf editor.

Press Alt+F2 and run
```

gconf-editor

```
Navigate to the key:
```

apps -> gnome-power-manager -> Lock

```
And untick the 'suspend' box, make sure the 'use_screensaver_settings' is also un ticked.
Close the gconf-editor and it should work for you.

---

### Post by diilbert on 2008-07-17
Appreciate the quick reply!

---

