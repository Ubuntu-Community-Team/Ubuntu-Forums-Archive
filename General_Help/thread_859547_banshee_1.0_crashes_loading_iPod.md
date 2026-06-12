---
title: "banshee 1.0 crashes loading iPod"
date: 2008-07-14
forum: General Help
---

### Post by slugicide on 2008-07-14
Hey, whenever I try and load songs onto my iPod with banshee-1 it crashes.  I get this:
```
[Info  14:21:44.430] Running Banshee 1.0.0
[Info  14:21:46.419] Querying MusicBrainz for Disc Release (Db3nhA5ZOXQnAglVkH7GlyS_6_w-)
[Info  14:21:46.820] All services are started 2.146681s
[Info  14:21:48.473] nereid Client Started
[Info  14:21:48.852] Query finished (success: True, 2.433201 seconds)
Creating fresh track db: /media/IPOD/iPod_Control/iTunes/iTunesDB
Exception in Gtk# callback delegate
  Note: Applications can use GLib.ExceptionManager.UnhandledException to handle the exception.
System.NullReferenceException: Object reference not set to an instance of an object
  at Banshee.Gui.Widgets.UserJobTile.UpdateFromJob () [0x00218] in /build/buildd/banshee-1-1.0.0/src/Core/Banshee.ThickClient/Banshee.Gui.Widgets/UserJobTile.cs:193 
  at Banshee.Gui.Widgets.UserJobTile.UpdateFromJobTimeout () [0x00000] in /build/buildd/banshee-1-1.0.0/src/Core/Banshee.ThickClient/Banshee.Gui.Widgets/UserJobTile.cs:263 
  at GLib.Timeout+TimeoutProxy.Handler () [0x00000] 
   at GLib.ExceptionManager.RaiseUnhandledException(System.Exception e, Boolean is_terminal)
   at GLib.Timeout+TimeoutProxy.Handler()
   at GLib.Timeout+TimeoutProxy.Handler()
   at Gtk.Application.gtk_main()
   at Gtk.Application.gtk_main()
   at Gtk.Application.Run()
   at Banshee.Gui.GtkBaseClient.Run() in /build/buildd/banshee-1-1.0.0/src/Core/Banshee.ThickClient/Banshee.Gui/GtkBaseClient.cs:line 114
   at Banshee.Gui.GtkBaseClient.Startup() in /build/buildd/banshee-1-1.0.0/src/Core/Banshee.ThickClient/Banshee.Gui/GtkBaseClient.cs:line 55
   at Hyena.Gui.CleanRoomStartup.Startup(Hyena.Gui.StartupInvocationHandler startup) in /build/buildd/banshee-1-1.0.0/src/Libraries/Hyena.Gui/Hyena.Gui/CleanRoomStartup.cs:line 54
   at Banshee.Gui.GtkBaseClient.Entry() in /build/buildd/banshee-1-1.0.0/src/Core/Banshee.ThickClient/Banshee.Gui/GtkBaseClient.cs:line 50
   at Nereid.Client.Main(System.String[] args) in /build/buildd/banshee-1-1.0.0/src/Clients/Nereid/Nereid/Client.cs:line 77
```
Any idea what's wrong?  Thanks.

---

