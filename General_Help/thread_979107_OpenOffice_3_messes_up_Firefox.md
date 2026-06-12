---
title: "OpenOffice 3 messes up Firefox"
date: 2008-11-11
forum: General Help
---

### Post by PropheticAngel on 2008-11-11
I recently tried to install openoffice 3, and after I installed via the debs, Firefox would turn on with an ubiquity error.  I then removed ubiquity to solve that, but I have no bookmarks.  

DPKG was locked and I used the suggestion from another thread to fix that, but I have no idea where to go from here to fix firefox bookmarks.

EDIT: I also realize I can not use the stop, refresh, back or forward buttons.
EDIT2: I simply made a new profile, moved my bookmark backups from the old profile, and did a partial update as via suggestion by update-manager.  This seems to work now, but does anyone know a method where you can save the old profile instead of making a new one?

---

### Post by ajgreeny on 2008-11-11
Which version of ubuntu and how exactly did you install the OOo3?  If you used the .deb tar.gz  from the OO website and installed everything in the DEBS folder with ```
sudo dpkg -i *.deb
``` it should work OK.  I did exactly that and had no difficulty at all.  OOo3 and FF3 both work beautifully, so it must be something you did or your different setup.

---

