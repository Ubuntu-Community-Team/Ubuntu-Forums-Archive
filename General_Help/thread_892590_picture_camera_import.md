---
title: "picture camera import"
date: 2008-08-17
forum: General Help
---

### Post by benste on 2008-08-17
Hy, I'm not able to import my pics anymore from a canaon powershot A85.
There popups a windows which asks me what I want to do with the cam and afterwars there doesn't appear anything.

I heard that the camera import is using f-spot so I tried to start f-spot manually which ended in a couple of errors whcih i don#t understand.
So what do I have to do so that f-spot works again (already reinstalled via synaptics)

```
benste@vaiofe31m:~$ f-spot
System.ApplicationException: F-Spot cannot find the Dbus session bus.  Make sure dbus is configured properly or start a new session for f-spot using "dbus-launch f-spot" ---> System.Exception: Unable to open the system message bus. ---> System.DllNotFoundException: libc
  at (wrapper managed-to-native) NDesk.DBus.Transports.UnixSocket:socket (int,int,int)
  at NDesk.DBus.Transports.UnixSocket..ctor () [0x00000] 
  at NDesk.DBus.Transports.UnixNativeTransport.OpenUnix (System.String path) [0x00000] 
  at NDesk.DBus.Transports.UnixNativeTransport.Open (System.String path, Boolean abstract) [0x00000] 
  at NDesk.DBus.Transports.UnixTransport.Open (NDesk.DBus.AddressEntry entry) [0x00000] 
  at NDesk.DBus.Transports.Transport.Create (NDesk.DBus.AddressEntry entry) [0x00000] 
  at NDesk.DBus.Connection.OpenPrivate (System.String address) [0x00000] 
  at NDesk.DBus.Connection..ctor (System.String address) [0x00000] 
  at NDesk.DBus.Bus..ctor (System.String address) [0x00000] 
  at NDesk.DBus.Bus.Open (System.String address) [0x00000] 
  at NDesk.DBus.Bus.get_System () [0x00000] --- End of inner exception stack trace ---

  at NDesk.DBus.Bus.get_System () [0x00000] 
  at NDesk.DBus.BusG.Init () [0x00000] 
  at FSpot.Driver.Main (System.String[] args) [0x00000] --- End of inner exception stack trace ---

  at FSpot.Driver.Main (System.String[] args) [0x00000] 

Unhandled Exception: System.DllNotFoundException: intl
  at (wrapper managed-to-native) Mono.Unix.Catalog:gettext (intptr)
  at Mono.Unix.Catalog.GetString (System.String s) [0x00000] 
  at FSpot.UI.Dialog.ExceptionDialog.BuildExceptionMessage (System.Exception e) [0x00000] 
  at FSpot.UI.Dialog.ExceptionDialog..ctor (System.Exception e) [0x00000] 
  at FSpot.Driver.Main (System.String[] args) [0x00000] 

Unhandled Exception: System.DllNotFoundException: msvcrt
  at (wrapper managed-to-native) Mono.Unix.Native.Stdlib:free (intptr)
  at Mono.Unix.UnixMarshal.FreeHeap (IntPtr ptr) [0x00000] 
  at Mono.Unix.Catalog.GetString (System.String s) [0x00000] 
  at FSpot.UI.Dialog.ExceptionDialog.BuildExceptionMessage (System.Exception e) [0x00000] 
  at FSpot.UI.Dialog.ExceptionDialog..ctor (System.Exception e) [0x00000] 
  at FSpot.Driver.Main (System.String[] args) [0x00000] 

```

---

### Post by benste on 2008-08-18
There are similar errors for a couple of programs on my computer,
like this one for gnome-rdp
```
benste@vaiofe31m:~$ gnome-rdp

Unhandled Exception: System.DllNotFoundException: intl
  at (wrapper managed-to-native) Mono.Unix.Catalog:bindtextdomain (intptr,intptr)
  at Mono.Unix.Catalog.Init (System.String package, System.String localedir) [0x00000] 
  at GnomeRDP.MainApp..ctor (System.String[] args) [0x00000] 
  at GnomeRDP.MainApp.Main (System.String[] args) [0x00000] 

Unhandled Exception: System.DllNotFoundException: msvcrt
  at (wrapper managed-to-native) Mono.Unix.Native.Stdlib:free (intptr)
  at Mono.Unix.UnixMarshal.FreeHeap (IntPtr ptr) [0x00000] 
  at Mono.Unix.Catalog.Init (System.String package, System.String localedir) [0x00000] 
  at GnomeRDP.MainApp..ctor (System.String[] args) [0x00000] 
  at GnomeRDP.MainApp.Main (System.String[] args) [0x00000] 

```

+ at shutdown there are errors with GDM + Dbus and Network-manager+ dbus

Please Help me !!

---

### Post by benste on 2008-08-25
I 'm sorry, but there is still no one who knows anything about these dbus things?

---

