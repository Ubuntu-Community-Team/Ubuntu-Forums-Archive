---
title: "cairo dock warning :  (cairo-dock-keybinder.c:cd_keybinder_bind:301)"
date: 2008-08-20
forum: General Help
---

### Post by trillions on 2008-08-20
i get this when i try to open cairo-dock in terminal:

joshua@robot:~$ cairo-dock
_cd_find_volume_name_from_drive_name: assertion `pDrive != NULL' failed
_cd_find_volume_name_from_drive_name: assertion `pDrive != NULL' failed
Binding '<Shift><Ctrl>F3' failed!
warning :  (cairo-dock-keybinder.c:cd_keybinder_bind:301)  
  couldnt bind <Shift><Ctrl>F3

i've followed other threads on how to install this apt, and it did work, once...but now is FAIL.

could someone translate?
tell me what i need to tell you...
i have the .deb files. i have also tried to install from repos.
both have failed
(i have 32bit 8.04 hardy)
thanks

---

### Post by fabounet on 2008-08-20
seems it doesn't manage to bind this keyboard shortcut.
just try to change it (this one is the default for the terminal applet or the alsaMixer applet)
it's not a critical error though.

---

### Post by trillions on 2008-08-20
thats all it says in the terminal...and cairo won't start...am i missing something?

---

### Post by trillions on 2008-08-20
ok, i've reinstalled and now:

joshua@robot:~$ cairo-dock
warning :  (cairo-dock-application-factory.c:cairo_dock_create_surface_from_xpixmap:120)  
  This pixmap is undefined. It can happen for exemple for a window that is in a minimized state when the dock is launching.
_cd_find_volume_name_from_drive_name: assertion `pDrive != NULL' failed
_cd_find_volume_name_from_drive_name: assertion `pDrive != NULL' failed
Binding '<Shift><Ctrl>F3' failed!
warning :  (cairo-dock-keybinder.c:cd_keybinder_bind:301)  
  couldnt bind <Shift><Ctrl>F3

???

---

### Post by prshah on 2008-08-20
> **trillions said:**
> thats all it says in the terminal...and cairo won't start...am i missing something?

Are you running a desktop compositor (such as compiz)?

---

### Post by trillions on 2008-08-20
yes compiz.

---

### Post by trillions on 2008-08-20
ok, i ran this:

sudo apt-get purge cairo-dock

then reinstalled.

works fine now.

[SOLVED]

---

