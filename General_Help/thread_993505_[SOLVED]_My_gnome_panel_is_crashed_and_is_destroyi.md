---
title: "[SOLVED] My gnome panel is crashed and is destroying my system!"
date: 2008-11-25
forum: General Help
---

### Post by josephellengar on 2008-11-25
Both are staying on the bottom.  When I am logged in to gnome I can't get any response even right-click out of any of my gnome panels.  Also, I can't use alt-f2 in gnome.  Right now, I am unable to do anything in gnome at all.  I have to use xfce.  This happened when I changed one of the settings in the panel.  I can't remember what it was.  It would help if there were some way to turn off gnome panel and keep it off, maybe?  I've tried reinstalling it and all of its dependencies.

---

### Post by decard_pain on 2008-11-25
when you uninstalled all the gnome packages did you also purge the setting for the packages
also remember just uninstalling the ubuntu-desktop package actually uninstalls nothing it's a meta package

just uninstalling the packages leaves the settings intact .
best way is to completely remove them with the synaptic 
just right click the package in synaptic and mark for complete removal 

hope this helps

---

### Post by josephellengar on 2008-11-25
It didn't work.  I get this error pretty much no matter what packages I have installed along with gnome-panel.  Here's the error message I'm getting when this happens:

(gnome-panel:9379): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -4 and height 24

** (gnome-panel:9379): CRITICAL **: panel_applet_frame_change_background: assertion `PANEL_IS_WIDGET (GTK_WIDGET (frame)->parent)' failed

(gnome-panel:9379): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -158 and height 24

(gnome-panel:9379): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -158 and height 24

(gnome-panel:9379): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -158 and height 24

(gnome-panel:9379): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -158 and height 24

(gnome-panel:9379): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -158 and height 24

---

### Post by decard_pain on 2008-11-25
this is a little beyond me I'm afraid.somebody with more knowledge of the pannels and how they work is required i think..sorry i couldn't be more help

---

