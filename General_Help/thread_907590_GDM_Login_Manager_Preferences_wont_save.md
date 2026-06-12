---
title: "GDM Login Manager Preferences wont save"
date: 2008-09-01
forum: General Help
---

### Post by spectre_hfx on 2008-09-01
.

---

### Post by spectre_hfx on 2008-09-04
.

---

### Post by thehkv on 2008-09-08
Facing same problem ... found any solution ??

---

### Post by spectre_hfx on 2008-09-11
.

---

### Post by djacidjac on 2008-09-24
I had a similar problem; no changes to "Login Window" would save. I deleted /etc/gdm/gdm.conf-custom and then made a copy of /etc/gdm/gdm.conf named gdm.conf-custom. Everything works in "Login Window" now. Just remember that any changes you made in the past will be gone and you'll be left with the default settings. 

This took me a while to figure out. I hope this helps.

---

### Post by djacidjac on 2008-09-24
I had a similar problem; no changes to "Login Window" would save. I deleted /etc/gdm/gdm.conf-custom and then made a copy of /etc/gdm/gdm.conf named gdm.conf-custom. Everything works in "Login Window" now. Just remember that any changes you made in the past will be gone and you'll be left with the default settings.

This took me a while to figure out. I hope this helps.

---

