---
title: "No desktop icons/wallpaper"
date: 2008-08-01
forum: General Help
---

### Post by diaz028 on 2008-08-01
-Hardy-

Cannot right-click on desktop either. Everything else works, applications, panels, terminal, nautilus. Desktop effects such as wobble and explosions are fine as well.

Ideas?

Thank you!

---

### Post by Choad on 2008-08-01
> **diaz028 said:**
> -Hardy-

Cannot right-click on desktop either. Everything else works, applications, panels, terminal, nautilus. Desktop effects such as wobble and explosions are fine as well.

Ideas?

Thank you!
nautilus bugged out when you started up. log out and log back in again, it'll probably work

---

### Post by northern lights on 2008-08-01
Sounds like nautilus has been set to not draw the desktop.

Run```
gconf-editor
```and navigate to '/apps/nautilus/preferences' is 'Show Desktop' unchecked?

---

