---
title: "[SOLVED] metacity and compiz"
date: 2008-09-06
forum: General Help
---

### Post by pikabuntu on 2008-09-06
HI, whenever I start compiz, it starts  emerald. I want to switch to metacity, but whenever I do, it turns compiz back off, and so on.

How could I start metacity without shutting down compiz?

---

### Post by vishzilla on 2008-09-06
Remove Emerald is one solution
Other is Alt+F2 and enter metacity --replace

---

### Post by pikabuntu on 2008-09-06
metacity --replace is what i have been doing :(

---

### Post by brownknight on 2008-09-06
Huh? I thought you can only have one running at any time - either you use Metacity or Compiz. When you turn on Compiz, you close Metacity and vice versa. Others please correct me if im wrong.

---

### Post by vishzilla on 2008-09-06
> **pikabuntu said:**
> metacity --replace is what i have been doing :(
Try removing emerald

---

### Post by pikabuntu on 2008-09-06
that did the trick :)

---

### Post by pikabuntu on 2008-09-06
> **brownknight said:**
> Huh? I thought you can only have one running at any time - either you use Metacity or Compiz. When you turn on Compiz, you close Metacity and vice versa. Others please correct me if im wrong.
metacity, emerald, etc. are window managers
compiz is the special effects

---

### Post by rossjman1 on 2008-09-06
If you have Compiz Fusion Icon installed you can right click on it and change window decorator from Emerald to GTK Window Decorator. No need to uninstall Emerald.

---

### Post by ad_267 on 2008-09-07
Yeah or "gtk-window-decorator --replace"

---

