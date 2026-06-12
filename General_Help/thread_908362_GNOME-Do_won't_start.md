---
title: "GNOME-Do won't start"
date: 2008-09-02
forum: General Help
---

### Post by xjgnsdof on 2008-09-02
When I run GNOME-Do from the command line, I get the following output:

```
** (Do:3862): CRITICAL **: gnome_desktop_item_get_localestring: assertion `item != NULL' failed

** (Do:3862): CRITICAL **: gnome_desktop_item_get_localestring: assertion `item != NULL' failed

** (Do:3862): CRITICAL **: gnome_desktop_item_get_string: assertion `item != NULL' failed

** (Do:3862): CRITICAL **: gnome_desktop_item_get_string: assertion `item != NULL' failed
Universe contains 90 items.
```

I installed the app using the instructions from the official wiki.

---

### Post by xjgnsdof on 2008-09-03
up

---

### Post by xjgnsdof on 2008-09-09
up

---

### Post by pdadad on 2009-07-16
I was able to go to /<home folder>/.local/share/gnome-do/plugins-0.6.0/addin-db-001/addin-data/global and delete the plugin that was causing gnome-do to shut down.

---

