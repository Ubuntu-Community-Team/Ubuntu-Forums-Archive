---
title: "[SOLVED] Removing App from MenuBar"
date: 2008-09-06
forum: General Help
---

### Post by sheepop39 on 2008-09-06
I can't seem to remove an app from the menu bar and it installed through wine and and now I can't seem to be able to remove it from the menubar after I uninstalled the app, anyone have an idea what to do

---

### Post by lovinglinux on 2008-09-06
> **happyhamster said:**
> Both the .config and .local folders in your home dir store wine-menu related stuff. (Press ctrl-h in nautilus to be able to see hidden files.)

For example:
.config/menus/applications-merged
.local/share/desktop-directories

And you'll probably have to restart gnome-panel or such to see any changes (press  ctrl-alt-backspace for example; this will close all programs though. Perhaps "killall gnome-panel" works also.)

Open the directories listed in the quote above and delete the unwanted menus.

---

### Post by sheepop39 on 2008-09-06
thanks, it worked

---

### Post by lovinglinux on 2008-09-06
You are welcome. Please mark the thread as SOLVED using the "Thread Tools" menu.

---

