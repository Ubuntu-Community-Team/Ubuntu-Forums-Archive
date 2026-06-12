---
title: "Desktop empty?!"
date: 2008-08-29
forum: General Help
---

### Post by puurokauha on 2008-08-29
Story goes like this. We watched dvd movie with my girlfriend. Movie ended and I closed gxine (didn't notice nothing unusual). Went to bathroom and then my girlfriend says that desktop is empty. I thought that my hdd is spinning its last rounds, because it has been acting strangely. I opened console and checked desktop, all files are there. Backup... Some google. Then gconf-editor, apps/nautilus/preferences show_desktop is checked, tried to uncheck it and logout, no good. And of course couple of shutdowns and restarts between this and that. So how do I get my desktop back?

---

### Post by spiderbatdad on 2008-08-29
```
sudo /etc/init.d/gdm restart
```

---

### Post by puurokauha on 2008-08-29
That worked, thank you.

---

### Post by spiderbatdad on 2008-08-29
You are very welcome.
I'm sorry I don't know why your desktop session crashed. Maybe someone else knows the answer to that issue.

---

