---
title: "[SOLVED] Laptop LCD Brightness Setting"
date: 2008-09-26
forum: General Help
---

### Post by russlar on 2008-09-26
Hello Forum,

Back in Gutsy, there was a feature in the Power Management that allowed me to set a default brightness for the LCD. Is this still a feature in Hardy? If so, how do I access it? The Power Management app no longer has this option.

---

### Post by mikewhatever on 2008-09-26
The GUI options has been removed by either Gnome or Ubuntu devs. You can still access it through gconf-editor. Press alt+f2, type gconf-editor, navigate to apps->gnome-power-manager->backlight, and set the brightness you want for AC and battery

---

### Post by russlar on 2008-09-26
> **mikewhatever said:**
> The GUI options has been removed by either Gnome or Ubuntu devs. :confused:

thanks for the fix.

---

