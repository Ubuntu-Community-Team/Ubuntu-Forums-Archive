---
title: "[SOLVED] Problem with KDM Theme Manager, Plaese Help"
date: 2008-10-10
forum: General Help
---

### Post by Solarplight on 2008-10-10
I had edited my login screen through the login manager, now I have donloaded a kdm theme and installed it through the theme manager, but i still get the same login screen i had before.  I have the enable theme manager box checked.  Does anybody know what the problem might be?

---

### Post by Solarplight on 2008-10-11
Bump

---

### Post by Solarplight on 2008-10-12
Bump

---

### Post by Denestria on 2008-10-12
Check the file /etc/kde3/kdm/kdmrc to make sure that

usetheme=true
and
theme=/the/path/to/the/new/theme

if those are correct then check the directory /etc/default/kdm.d for files like 20_kubuntu_default_settings or 30_kubuntu_default_settings which can override you settings, remove or rename them to a backup if you like.  Then restart KDM, from the login window open the system menu and chose restart x.

---

### Post by Solarplight on 2008-10-21
I changed the Theme= line in kdmrc and that worked fine.

Thank You

---

