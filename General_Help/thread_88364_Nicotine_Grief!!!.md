---
title: "Nicotine Grief!!!"
date: 2005-11-10
forum: General Help
---

### Post by Mosey on 2005-11-10
Whenever I attempt to run Nicotine it opens up but then locks and I have to force quit the app.

When I run it in the terminal I recieve this error:

[I]self.hbox141.pack_start(self.vbox97, gtk.TRUE, gtk.FALSE, 0)
/usr/lib/site-python/pynicotine/gtkgui/settings_glade.py:1577: GtkDeprecationWarning: gtk.TRUE is deprecated, use True instead
  self.vbox91.pack_start(self.hbox141, gtk.TRUE, gtk.TRUE, 0)
/usr/lib/site-python/pynicotine/gtkgui/settings_glade.py:1579: GtkDeprecationWarning: gtk.FALSE is deprecated, use False instead
  self.hbox146 = gtk.HBox(gtk.FALSE, 0)
/usr/lib/site-python/pynicotine/gtkgui/settings_glade.py:1584: GtkDeprecationWarning: gtk.FALSE is deprecated, use False instead
  self.UseCustomBan.set_active(gtk.FALSE)
/usr/lib/site-python/pynicotine/gtkgui/settings_glade.py:1588: GtkDeprecationWarning: gtk.FALSE is deprecated, use False instead
  self.hbox146.pack_start(self.UseCustomBan, gtk.FALSE, gtk.FALSE, 0)
/usr/lib/site-python/pynicotine/gtkgui/settings_glade.py:1592: GtkDeprecationWarning: gtk.TRUE is deprecated, use True instead
  self.CustomBan.set_editable(gtk.TRUE)
/usr/lib/site-python/pynicotine/gtkgui/settings_glade.py:1594: GtkDeprecationWarning: gtk.TRUE is deprecated, use True instead
  self.hbox146.pack_start(self.CustomBan, gtk.TRUE, gtk.TRUE, 0)
/usr/lib/site-python/pynicotine/gtkgui/settings_glade.py:1596: GtkDeprecationWarning: gtk.FALSE is deprecated, use False instead
  self.vbox91.pack_start(self.hbox146, gtk.FALSE, gtk.FALSE, 0)
/usr/lib/site-python/pynicotine/gtkgui/settings_glade.py:1606: GtkDeprecationWarning: gtk.FALSE is deprecated, use False instead
  if create:
/usr/lib/site-python/pynicotine/gtkgui/settings_glade.py:777: GtkDeprecationWarning: gtk.FALSE is deprecated, use False instead
  if create:
/usr/lib/site-python/pynicotine/gtkgui/settings_glade.py:788: GtkDeprecationWarning: gtk.FALSE is deprecated, use False instead
  self.vbox86 = gtk.VBox(gtk.FALSE, 10)
/usr/lib/site-python/pynicotine/gtkgui/settings_glade.py:794: GtkDeprecationWarning: gtk.FALSE is deprecated, use False instead
  self.TabClosers.set_active(gtk.FALSE)
[/I]

That stuff goes on for a few more pages.

Any thoughts? This has been happening for a few days.

---

### Post by ow50 on 2005-11-10
[QUOTE=Mosey]Whenever I attempt to run Nicotine it opens up but then locks and I have to force quit the app.

When I run it in the terminal I recieve this error:

GtkDeprecationWarning: gtk.TRUE is deprecated, use True instead
GtkDeprecationWarning: gtk.FALSE is deprecated, use False instead
[/QUOTE]
Those are deprecation warnings and they won't cause any freezing. You probably won't get any output on whatever is causing the freezing. My experience is that Nicotine freezes for about a minute or so, but regains responsiveness for a while and the freezes again and so on. I reckon it's just bad code and nothing you can do about it.

---

