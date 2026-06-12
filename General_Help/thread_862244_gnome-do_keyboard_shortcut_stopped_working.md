---
title: "gnome-do keyboard shortcut stopped working"
date: 2008-07-17
forum: General Help
---

### Post by richtl on 2008-07-17
I have gnome-do mapped to my Menu key in gconf:/apps/gnome-do/preferences, but after yesterday's Update Manager updates it stopped working. Gnome-do is running quietly in the background, as it always has, but will no longer respond to the keypress.

I tried remapping the key binding to the default and restarting Do, but it still doesn't work. I can, however, run gnome-do from the command line or map the command to a key, but that's not optimal, since it has to relaunch Do each time and is very slow.

---

### Post by richtl on 2008-07-18
Just started working again two days later. Whatever.

---

### Post by -al on 2008-07-29
This just happened to me, as well. I installed the upgrades and now I can't summon gnome-do.
Has anyone else had this problem?

---

### Post by munkymac on 2008-08-04
> **-al said:**
> This just happened to me, as well. I installed the upgrades and now I can't summon gnome-do.
Has anyone else had this problem?

I'm having the same problem as well. When I try to run Gnome-Do from the terminal, this is what I get:

```
aaron@aaron-laptop:~$ gnome-do
No account info stored for GMailContacts.GMailConfig
GMailContacts Error: Invalid credentials
Universe contains 3857 items.
Exception in Gtk# callback delegate
  Note: Applications can use GLib.ExceptionManager.UnhandledException to handle the exception.
System.TypeInitializationException: An exception was thrown by the type initializer for Notifications.Notification ---> System.Exception: Unable to open the session message bus. ---> System.ArgumentNullException: Argument cannot be null.
Parameter name: address
  at NDesk.DBus.Bus.Open (System.String address) [0x00000] 
  at NDesk.DBus.Bus.get_Session () [0x00000] --- End of inner exception stack trace ---

  at NDesk.DBus.Bus.get_Session () [0x00000] 
  at NDesk.DBus.BusG.Init () [0x00000] 
  at Notifications.Notification..cctor () [0x00000] --- End of inner exception stack trace ---

  at Do.UI.NotificationIcon.ShowNotification (System.String title, System.String message, System.String icon) [0x00000] 
  at Do.UI.NotificationIcon+<>c__CompilerGenerated15.<SendNotification>c__42 (System.Object +16, System.EventArgs +17) [0x00000] 
  at Gtk.Application+InvokeCB.Invoke () [0x00000] 
  at GLib.Timeout+TimeoutProxy.Handler () [0x00000] 
   at GLib.ExceptionManager.RaiseUnhandledException(System.Exception e, Boolean is_terminal)
   at GLib.Timeout+TimeoutProxy.Handler()
   at GLib.Timeout+TimeoutProxy.Handler()
   at Gtk.Application.gtk_main()
   at Gtk.Application.gtk_main()
   at Gtk.Application.Run()
   at Do.Do.Main(System.String[] args)

```

---

### Post by ben2talk on 2008-11-08
Gnome-do is THE killer application for me so far in Ubuntu. There are many things I love and hate - and although I would never run Vista again, and only use XP in a virtual box - I still miss the reliability.

Why is it that I can have two instances of gnome-do running? Why does the shortcut fail to function? Why does the icon fail to appear sometimes?

It wouldn't be so bad if the icon was reliable - at least it would be partly functional!

---

### Post by GriFF3n on 2009-02-09
Having the same problem after I updated to .8. Made a new post about it. Did you ever figure it out?

GriFF

---

### Post by WatsonJX on 2009-02-20
Same thing here. 0.6 was running OK but after I upgraded to 0.8 gnome-do gnome-do-plugins from launchpad PPA, I got dbus error, and Win+SPACE stopped working.

~$ gnome-do
[Error 11:46:47.674] [SystemService] Could not initialize dbus: Unable to open the session message bus.
[Error 11:46:48.083] Could not load desktop item: Unknown encoding of: file:///usr/share/applications/lynx.desktop
[Error 11:46:48.173] [SystemService] Could not GetOnBattery: Unable to open the session message bus.

My another box (dist-upgraded from Ubuntu 8.04 to 8.10) is OK though.

I don't want to dist-upgrade this box....

---

