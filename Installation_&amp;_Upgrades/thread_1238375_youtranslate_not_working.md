---
title: "youtranslate not working"
date: 2009-08-12
forum: Installation &amp; Upgrades
---

### Post by JvdS45 on 2009-08-12
Hi get this following message by starting up youtranslate 64 amd machine

Exception in Gtk# callback delegate
  Note: Applications can use GLib.ExceptionManager.UnhandledException to handle the exception.
System.DllNotFoundException: gdk-x11-2.0
  at (wrapper managed-to-native) TrayIcon:gdk_x11_display_get_xdisplay (intptr)
  at TrayIcon.OnRealized () [0x00000] 
  at Gtk.Widget.realized_cb (IntPtr widget) [0x00000] 
   at GLib.ExceptionManager.RaiseUnhandledException(System.Exception e, Boolean is_terminal)
   at Gtk.Widget.realized_cb(IntPtr widget)
   at Gtk.Widget.gtk_widget_show_all(IntPtr )
   at Gtk.Widget.ShowAll()
   at YTTrayIcon..ctor(Gtk.Window mwin, .ytApp y)
   at ytApp.setupGUI()
   at ytApp..ctor(System.String[] args)
   at ytApp.Main(System.String[] args)
What is going on and what can I do to repair this btw it never runs

thanks

Johan

---

