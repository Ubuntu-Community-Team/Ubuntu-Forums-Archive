---
title: "[SOLVED] Python apps won't run 8.10"
date: 2008-12-07
forum: Installation &amp; Upgrades
---

### Post by Amzo2 on 2008-12-07
Hello, for some reason I can't run python applications, well some. I recently compiled gtk+ 2.12.12 from source and installed quite a few engines. 

When I run applications that require python I get various errors:

emesene I got

ImportError: /var/lib/python-support/python2.5/gtk-2.0/gtk/_gtk.so: undefined symbol: gtk_font_selection_get_preview_entry

gedit runs, but when I try to open a file I get...

gedit: symbol lookup error: gedit: undefined symbol: gtk_icon_theme_lookup_by_gicon

Those are mainly the two errors that come up for other apps that I try to run. Does anyone have any idea?

---

### Post by ibutho on 2008-12-07
Welcome to the forums.

The version of python-gtk2 on your system is probably configured for the gtk2 version shipped by Ubuntu and not the one you compiled yoursel. You may need to compile your own version of python-gtk2 for the version of gtk2 you installed. Out of curiosity why did you have to compile gtk2 from source?

---

### Post by Amzo2 on 2008-12-07
I compiled gtk+ from source because Something was saying I didn't have the required gtk, and at the time i didn't realize gt2 was the same ¬.¬ and couldn't find gtk+ in the apt list. xD

---

### Post by Amzo2 on 2008-12-07
Yeah it is working now, thanks a lot. it fixed my first error but I had to install python-gobject-dbg after because it gave another errors (just incase other people have this problem) and it's working now. :D

---

