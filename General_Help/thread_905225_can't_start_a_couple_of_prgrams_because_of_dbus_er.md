---
title: "can't start a couple of prgrams because of dbus errors!! PLease help"
date: 2008-08-30
forum: General Help
---

### Post by benste on 2008-08-30
hy together,
shortly: I can't launch f-spot or gnome-rdp, but i need both asap.
The terminal output looks like this:
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

and now gnome-rdp:
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
benste@vaiofe31m:~$ 


```
If you have any ideas please answer asap
- I already tried to install all d-bus related programs including f-spot and gnome-rdp but the error is still the same.

---

### Post by MentalNotes on 2008-08-30
Looks like you might have been bitten by this bug here: [https://bugs.launchpad.net/ubuntu/+source/f-spot/+bug/89832](https://bugs.launchpad.net/ubuntu/+source/f-spot/+bug/89832)
Try installing the dbus-x11 package and logging out then back in again.

---

### Post by benste on 2008-08-30
I'm sorry, but it's still the same:


my Dbus Version is:
1.1.20-1ubuntu2

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

### Post by MentalNotes on 2008-08-30
It sounds like dbus isn't running. Could you please post the output of ```
env | grep dbus
```

---

### Post by benste on 2008-08-30
here it is:
```
benste@vaiofe31m:~$ env | grep dbus
DBUS_SESSION_BUS_ADDRESS=unix:abstract=/tmp/dbus-TQFGAp3xVl,guid=df36a2b522380d833e3b6ca448b920d9

```

---

### Post by MentalNotes on 2008-08-30
Hmm, so dbus is running. Could you please run ```
dbus-launch f-spot
``` and post the output.

---

### Post by benste on 2008-08-30
Here again :)```

benste@vaiofe31m:~$ dbus-launch f-spot
Unable to create /home/benste/.dbus/session-bus
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

### Post by benste on 2008-08-30
because of unable to create I tried sudo and your command:
result a longer but different error :-)

```
benste@vaiofe31m:~$ sudo dbus-launch f-spot
[sudo] password for benste: 

(/usr/lib/f-spot/f-spot.exe:17452): GLib-GObject-CRITICAL **: /build/buildd/glib2.0-2.16.4/gobject/gtype.c:2248: initialization assertion failed, use IA__g_type_init() prior to this function

(/usr/lib/f-spot/f-spot.exe:17452): GLib-GObject-CRITICAL **: g_object_new: assertion `G_TYPE_IS_OBJECT (object_type)' failed

(/usr/lib/f-spot/f-spot.exe:17452): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed
Stacktrace:

  at (wrapper managed-to-native) GConf.Client.gconf_client_get_default () <0x00004>
  at (wrapper managed-to-native) GConf.Client.gconf_client_get_default () <0xffffffff>
  at GConf.Client..ctor () <0x0003b>
  at FSpot.GConfPreferenceBackend.get_Client () <0x0001f>
  at FSpot.GConfPreferenceBackend.AddNotify (string,FSpot.NotifyChangedHandler) <0x00033>
  at FSpot.Preferences.get_Backend () <0x000ea>
  at FSpot.Preferences.Get (string) <0x00074>
  at FSpot.Driver.Main (string[]) <0x00144>
  at (wrapper runtime-invoke) FSpot.Driver.runtime_invoke_int_string[] (object,intptr,intptr,intptr) <0xffffffff>

Native stacktrace:

	f-spot [0x816b1fa]
	f-spot [0x807de81]
	[0xb7eea440]
	/usr/lib/libgconf-2.so.4(gconf_client_get_default+0xa9) [0xb6b059f9]
	[0xb7672e28]
	[0xb76728c4]
	[0xb7672860]
	[0xb76727ac]
	[0xb767267b]
	[0xb76721c5]
	[0xb766e93d]
	[0xb766e1c4]
	f-spot(mono_runtime_exec_main+0x10e) [0x809c68e]
	f-spot(mono_runtime_run_main+0x173) [0x809c933]
	f-spot(mono_main+0x6a9) [0x805acd9]
	f-spot [0x805a122]
	/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7c93450]
	f-spot [0x805a091]

Debug info from gdb:

(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread 0xb7c3b940 (LWP 17452)]
[New Thread 0xb70ebb90 (LWP 17462)]
[New Thread 0xb766db90 (LWP 17461)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
0xb7eea410 in __kernel_vsyscall ()
  3 Thread 0xb766db90 (LWP 17461)  0xb7eea410 in __kernel_vsyscall ()
  2 Thread 0xb70ebb90 (LWP 17462)  0xb7eea410 in __kernel_vsyscall ()
  1 Thread 0xb7c3b940 (LWP 17452)  0xb7eea410 in __kernel_vsyscall ()

Thread 3 (Thread 0xb766db90 (LWP 17461)):
#0  0xb7eea410 in __kernel_vsyscall ()
#1  0xb7dfe196 in nanosleep () from /lib/tls/i686/cmov/libpthread.so.0
#2  0x08105c91 in ?? ()
#3  0xb7df64fb in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#4  0xb7d53e5e in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 2 (Thread 0xb70ebb90 (LWP 17462)):
#0  0xb7eea410 in __kernel_vsyscall ()
#1  0xb7dfaaa5 in pthread_cond_wait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x081088ff in ?? ()
#3  0x0810b3cd in ?? ()
#4  0x0810b43c in ?? ()
#5  0x0811ba1a in ?? ()
#6  0x080b1c0a in ?? ()
#7  0x080cef04 in ?? ()
#8  0x0811a7c2 in ?? ()
#9  0x081317a5 in ?? ()
#10 0xb7df64fb in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#11 0xb7d53e5e in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 1 (Thread 0xb7c3b940 (LWP 17452)):
#0  0xb7eea410 in __kernel_vsyscall ()
#1  0xb7d4c881 in select () from /lib/tls/i686/cmov/libc.so.6
#2  0xb7e7b2a4 in g_spawn_sync () from /usr/lib/libglib-2.0.so.0
#3  0xb7e7b66c in g_spawn_command_line_sync () from /usr/lib/libglib-2.0.so.0
#4  0x0816b295 in ?? ()
#5  0x0807de81 in ?? ()
#6  <signal handler called>
#7  0xb6b02423 in ?? () from /usr/lib/libgconf-2.so.4
#8  0xb6b059f9 in gconf_client_get_default () from /usr/lib/libgconf-2.so.4
#9  0xb7672e28 in ?? ()
#10 0xb76728c4 in ?? ()
#11 0xb7672860 in ?? ()
#12 0xb76727ac in ?? ()
#13 0xb767267b in ?? ()
#14 0xb76721c5 in ?? ()
#15 0xb766e93d in ?? ()
#16 0xb766e1c4 in ?? ()
#17 0x0809c68e in mono_runtime_exec_main ()
#18 0x0809c933 in mono_runtime_run_main ()
#19 0x0805acd9 in mono_main ()
#20 0x0805a122 in ?? ()
#21 0xb7c93450 in __libc_start_main () from /lib/tls/i686/cmov/libc.so.6
#22 0x0805a091 in ?? ()
#0  0xb7eea410 in __kernel_vsyscall ()


=================================================================
Got a SIGSEGV while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries 
used by your application.
=================================================================

Aborted

```

---

### Post by MentalNotes on 2008-08-30
Looks like your installation of mono is broken :( You might want to purge ("Completely Remove" in Synaptic) mono and related libraries (libmono, mono-common, etc.) and then reinstall them. If that doesn't help you could report it as a bug on Launchpad. Apart from that, I'm out of ideas sorry.

---

### Post by benste on 2008-08-30
I'll ask in the IRC channel first, there are several bugs in launchpad which says something about f-spot dbus and so on, I'm not shure where to post, but anyway thanks for your help.

---

