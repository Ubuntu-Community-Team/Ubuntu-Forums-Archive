---
title: "avant-window-navigator dont work"
date: 2008-09-14
forum: General Help
---

### Post by newbie- on 2008-09-14
i install that [http://thegabfather.wordpress.com/2008/05/29/71/](http://thegabfather.wordpress.com/2008/05/29/71/)

and when i hit System>Preferences>AWN Manager 
comes only setting thing, wheres that bar is?

terminal says:

a245@a245-desktop:~$ awn-manager
/usr/bin/awn-manager:65: GtkWarning: Attempting to read the recently used resources file at `/home/a245/.recently-used.xbel', but the parser failed: Virhe tiedoston "/home/a245/.recently-used.xbel" lukemisessa: Is a directory.
  self.wTree = gtk.glade.XML(self.GLADE_PATH, domain=defs.I18N_DOMAIN)
/usr/bin/awn-manager:65: Warning: g_bookmark_file_get_size: assertion `bookmark != NULL' failed
  self.wTree = gtk.glade.XML(self.GLADE_PATH, domain=defs.I18N_DOMAIN)
/usr/bin/awn-manager:65: GtkWarning: Error parsing gtk-icon-sizes string:
	'panel-menu=24,24
panel=20,20
gtk-button=18,18
gtk-large-toolbar=24,24'
  self.wTree = gtk.glade.XML(self.GLADE_PATH, domain=defs.I18N_DOMAIN)
/usr/bin/awn-manager:206: GtkWarning: Attempting to store changes into `/home/a245/.recently-used.xbel', but failed: Tiedoston "/home/a245/.recently-used.xbel.V560GU" uudelleen nimeäminen nimelle "/home/a245/.recently-used.xbel" epäonnistui: g_rename() epäonnistui: Is a directory
  gtk.main()
a245@a245-desktop:~$ 

i use hardy heron 8.04 LTS

what i do now? i really want that working!
sorry my bad english ;_;

---

### Post by howefield on 2008-09-14
Sorry, can't help with that specific problem, other than maybe try another dock ? cairo-dock is pretty good, imho.

---

### Post by fmartinez on 2008-09-14
You have to have Desktop Effects enabled, and need 3D acceleration enabled.

---

