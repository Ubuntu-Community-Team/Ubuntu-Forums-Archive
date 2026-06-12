---
title: "Removing Gnome Startup Programs (from the command line?)"
date: 2005-11-18
forum: General Help
---

### Post by suRoot on 2005-11-18
I just managed to do something really stupid.  I installed the thinkpad buttons package & added tpb to my gnome startup programs (under session -> startup programs).  After logging out & back in the splash screen goes as far as loading window manager & then hangs.  Apparently my thinkpad doesn't like this package :rolleyes: 

I need to remove this startup entry, but since I can't log in, I can't run gnome-update-session GUI.  I've been through all the gnome related directories in home & can't seem to find anything.  For the time being, I've just moved the gnome directories to a backup location & let gnome re-create them, which worked fine as I'm now logged in... but now I've lost a bunch of my preferences & settings.

Anyway, does anyone know of a command-line equivalent to gnome-update-session or where exactly gnome stores this info (what config file??)

Thanks!

---

### Post by suRoot on 2005-11-18
I found it:  **~/.gnome2/session-manual** contains the gnome startup programs.  Problem solved.

---

