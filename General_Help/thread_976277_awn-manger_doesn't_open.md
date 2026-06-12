---
title: "awn-manger doesn't open"
date: 2008-11-09
forum: General Help
---

### Post by catania on 2008-11-09
hello everybody,I have a problem with awn-manager.

launched from terminal:

```
giuseppe@rosario-desktop:~$ awn-manager
/usr/bin/awn-manager:64: GtkWarning: Impossibile trovare il motore del tema in module_path: «clearlooks»,
  self.wTree = gtk.glade.XML(self.GLADE_PATH, domain=defs.I18N_DOMAIN)
/usr/bin/awn-manager:64: GtkWarning: Impossibile trovare il motore del tema in module_path: «mist»,
  self.wTree = gtk.glade.XML(self.GLADE_PATH, domain=defs.I18N_DOMAIN)
/usr/bin/awn-manager:64: GtkWarning: GtkSpinButton: setting an adjustment with non-zero page size is deprecated
  self.wTree = gtk.glade.XML(self.GLADE_PATH, domain=defs.I18N_DOMAIN)
Traceback (most recent call last):
  File "/usr/bin/awn-manager", line 203, in <module>
    awnmanager = AwnManager()
  File "/usr/bin/awn-manager", line 104, in __init__
    self.make_menu_model()
  File "/usr/bin/awn-manager", line 140, in make_menu_model
    pixbuf = theme.load_icon("gtk-sort-ascending", 48, gtk.ICON_LOOKUP_FORCE_SVG)
glib.GError: Formato del file di immagine non riconosciuto
giuseppe@rosario-desktop:~$ 

```

why ???

bye

---

### Post by galenorama on 2008-11-09
I have a similar problem:
When I click on "AWN Manager" in the system preferences menu, nothing happens. I tried everything I could think of. The dock itself works great, but I just can't open the manager.
Help!

---

### Post by eternalnewbee on 2008-11-09
You cannot run AWN without compiz
(Check if your Hardware Driver is enabled: **Main Menu > System > Administration > Hardware Drivers**) If it is:
Press ALT-F2, and copy/paste this code: ```
compiz --replace
```

---

