---
title: "[SOLVED] GUI for changing locales"
date: 2008-09-15
forum: General Help
---

### Post by siddartha on 2008-09-15
How do you change locale settings in Gnome/Ubuntu?

---

### Post by siddartha on 2008-09-23
Either use the Language item from the System menu for all settings or read the locale man page and do: ```
sudo gedit /etc/environment
```
Beware, not all apps seem to be impressed by that one. For example LC_PAPER seems irelevant and /etc/papersize is preffered.

---

