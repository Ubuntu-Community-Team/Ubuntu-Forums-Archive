---
title: "F-Spot error on startup yet runs in sudo"
date: 2009-11-07
forum: Installation &amp; Upgrades
---

### Post by Dragonbite on 2009-11-07
I have installed Karmic on this laptop, but haven't gotten F-Spot to work yet.  There is a possible upgrade that was interrupted which may have borked the system but I don't know.

When I start up F-Spot I get this error message with Close as the only option. ```
An unhandled exception was thrown: Extension node not found in path: /FSpot/Sidebar

  at Mono.Addins.ExtensionContext.AddExtensionNodeHandler (System.String path, Mono.Addins.ExtensionNodeEventHandler handler) [0x00000] 
  at Mono.Addins.AddinManager.AddExtensionNodeHandler (System.String path, Mono.Addins.ExtensionNodeEventHandler handler) [0x00000] 
  at MainWindow..ctor (.Db db) [0x00000] 
  at FSpot.Core.get_MainWindow () [0x00000] 
  at FSpot.Core.Organize () [0x00000] 
  at FSpot.Driver.Main (System.String[] args) [0x00000] 
.NET Version: 2.0.50727.1433

Assembly Version Information:

System.Core (3.5.0.0)
FSpot.Bling (0.0.0.0)
pango-sharp (2.12.0.0)
gtk-sharp-beans (2.14.0.0)
FSpot.Widgets (0.0.0.0)
gnome-sharp (2.24.0.0)
System.Transactions (2.0.0.0)
System.Configuration (2.0.0.0)
System.Xml (2.0.0.0)
NDesk.DBus.Proxies (0.0.0.0)
gconf-sharp (2.24.0.0)
System.Data (2.0.0.0)
Mono.Data.SqliteClient (2.0.0.0)
FSpot.Query (0.0.0.0)
FSpot.JobScheduler (0.0.0.0)
gdk-sharp (2.12.0.0)
NDesk.DBus.GLib (1.0.0.0)
NDesk.DBus (1.0.0.0)
gnome-vfs-sharp (2.24.0.0)
Cms (0.0.0.0)
FSpot.Core (0.0.0.0)
FSpot.Platform (0.0.0.0)
Mono.Posix (2.0.0.0)
FSpot.Utils (0.0.0.0)
atk-sharp (2.12.0.0)
gtk-sharp (2.12.0.0)
Mono.Addins (0.4.0.0)
System (2.0.0.0)
Mono.Addins.Setup (0.4.0.0)
glib-sharp (2.12.0.0)
f-spot (0.6.1.4)
mscorlib (2.0.0.0)

Platform Information: Linux 2.6.31-14-generic i686 unknown GNU/Linux

Distribution Information:

[/etc/debian_version]
squeeze/sid

[/etc/lsb-release]
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=9.10
DISTRIB_CODENAME=karmic
DISTRIB_DESCRIPTION="Ubuntu 9.10"


```

When I run F-Spot from the terminal using # sudo f-spot I get the following output, but the application does start up.```
** No session dbus found. Starting one **
[Info  10:01:51.005] Initializing DBus
[Info  10:01:51.338] Initializing Mono.Addins
[Info  10:01:54.274] Starting new FSpot server (f-spot 0.6.1.4)

** (f-spot:2030): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (f-spot:2030): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (f-spot:2030): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (f-spot:2030): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (f-spot:2030): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed
cleanup context
cleanup context

(f-spot:2030): GdkPixbuf-WARNING **: GdkPixbufLoader finalized without calling gdk_pixbuf_loader_close() - this is not allowed. You must explicitly end the data stream to the loader before dropping the last reference.
item ImportCommand+SourceItem
[Info  10:02:30.153] Starting BeagleService
[Info  10:02:30.203] Hack for gnome-settings-daemon engaged

(f-spot:2030): Gdk-WARNING **: losing last reference to undestroyed window

[Info  10:02:35.794] Exiting
drew@wyvern:~$ clear

drew@wyvern:~$ sudo f-spot
** No session dbus found. Starting one **
[Info  10:09:58.769] Initializing DBus
[Info  10:09:59.156] Initializing Mono.Addins
[Info  10:09:59.878] Starting new FSpot server (f-spot 0.6.1.4)

** (f-spot:2268): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (f-spot:2268): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (f-spot:2268): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (f-spot:2268): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (f-spot:2268): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed
[Info  10:10:04.908] Starting BeagleService
[Info  10:10:04.956] Hack for gnome-settings-daemon engaged

(f-spot:2268): GdkPixbuf-WARNING **: GdkPixbufLoader finalized without calling gdk_pixbuf_loader_close() - this is not allowed. You must explicitly end the data stream to the loader before dropping the last reference.
```

I have since tried Reinstalling F-Spot and even removing the F-Spot .deb file and forcing it to download it and reinstall it but to no avail.

---

### Post by Rytron on 2009-11-07
I too get an error, a different one though. The error is far too long to post here.

Also as with Dragonbite, f-spot starts with sudo.

I guess it is just a bug that needs to be sorted out with Karmic Koala.

---

### Post by oswallt on 2009-11-27
I am also getting a similar error, the same error on both my desktop which has been upgraded since dapper and my laptop which has a clean install.  Opening with sudo doesn't change anything for me.  F-spot pops up for a second and then immediately closes.  Fixes and work-arounds that I have seen in other posts of seemingly similar previous errors haven't worked.  Here is my error output:

```
~$ f-spot
[Info  23:23:18.448] Initializing DBus
[Info  23:23:18.563] Initializing Mono.Addins
[Info  23:23:18.733] Starting new FSpot server (f-spot 0.6.1.3)

** (f-spot:2198): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (f-spot:2198): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (f-spot:2198): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (f-spot:2198): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (f-spot:2198): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed
[Info  23:23:19.745] Starting BeagleService
[Info  23:23:19.762] Hack for gnome-settings-daemon engaged

(f-spot:2198): GdkPixbuf-WARNING **: GdkPixbufLoader finalized without calling gdk_pixbuf_loader_close() - this is not allowed. You must explicitly end the data stream to the loader before dropping the last reference.
The program 'f-spot' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 2979 error_code 11 request_code 53 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
```

---

### Post by carolinason on 2009-12-20
confirmed in karmic here. and they are thinking about removing gimp from the next release. i'm not sure if that's a good idea.

gwenview, however works like a champion.

i really could just get by with nautilus for the thumbnails, since i use gimp for all image editing. i bet gthumb would work too.
 
isn't f-spot a mono program? i guess that's an easy way to say No Wonder!

Actually gwenview is far superior than f-spot. i mean the fact that gwenview actually works makes it an easy call, but there are many things you can do in gwenview than in f-spot. i admit i haven't used f-spot in about a year.

---

### Post by alecwk on 2010-01-06
I had the same problem. Read somewhere that the Desktop Theme "New Wave" is having conflict with F-spot. 

I changed the Desktop Theme to "Dust" and F-spot launched with no problem. 

Try change your Desktop Theme.

---

### Post by Dragonbite on 2010-01-06
> **alecwk said:**
> I had the same problem. Read somewhere that the Desktop Theme "New Wave" is having conflict with F-spot. 

I changed the Desktop Theme to "Dust" and F-spot launched with no problem. 

Try change your Desktop Theme.

I'll try it out if I think of it.  

I just did a clean installation of 9.10 on a different desktop and it works fine, with no issues.

The installation that it didn't work was an upgrade from a relatively untouched (which means, I don't remember what I did an didn't do on that one), so I think that may have been a factor.

Thanks!

---

