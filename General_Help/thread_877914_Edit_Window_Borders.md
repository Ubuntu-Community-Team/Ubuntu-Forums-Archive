---
title: "Edit Window Borders??"
date: 2008-08-02
forum: General Help
---

### Post by armageddon08 on 2008-08-02
Is there any application to create/edit GTK window borders??
Also how can I get a glow effect in GTK borders??

---

### Post by sayakb on 2008-08-02
Most of the GTK themes are pixmap based. Find them in ~/.themes folder (/home/username/.themes) and edit the pixmaps in Gimp and give them a glow effect. The .themes folder is a hidden folder. Press Ctrl+H to show it..

---

### Post by armageddon08 on 2008-08-02
Can I do it in Widget Factory?

---

### Post by sayakb on 2008-08-02
I haven't quite used it (I don't use GTK themes). Maybe others can help you in this context..

---

### Post by armageddon08 on 2008-08-02
Is it possible to get the emerald glow effect in Metacity themes?

---

### Post by rainwalker on 2008-08-02
The Widget Factory is only to show what your current theme looks like. It can't be used to create themes; you do that by editing the gtkrc file (and pixmaps if necessary).

Metacity does have a small shadow around windows and menus, though I don't think it's configurable like Emerald's is (color, radius, opacity, etc.).

---

