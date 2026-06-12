---
title: "Double click options messed up"
date: 2008-08-14
forum: General Help
---

### Post by smmalis on 2008-08-14
If I double click on certain files (pdf, jpg, png) it said that there was no program for them, so I manually assigned them all (eog, evince, gedit, etc.), but it seems like almost all have been messed up.  Is there a way to reset them completely?

---

### Post by fragos on 2008-08-14
If you define messed up perhaps we can help.

---

### Post by smmalis on 2008-08-14
.txt files open in Firefox, .pdf files dont open ("No program associated with this file type"), .jpg files open in GIMP, etc.

---

### Post by pauper on 2008-08-14
Disclaimer: Paths among different Ubuntu versions may differ.

Compare etc/gnome/defaults.list to ~/.local/share/applications/defaults.list

Then:  /usr/share/applications/mimeinfo.cache and
~/.local/share/applications/mimeinfo.cache

Compare several strings:

> application/pdf=evince.desktop;
image/jpeg=gimp.desktop;eog.desktop;
text/plain=gedit.desktop;gvim.desktop;

Most likely ~/.local/share/applications/defaults.list is at fault. From here
it's up to you: overwrite, remove, or manually edit the mischievous one.

---

### Post by smmalis on 2008-08-14
~/.local/share/applications/defaults.list doesn't exist.

---

