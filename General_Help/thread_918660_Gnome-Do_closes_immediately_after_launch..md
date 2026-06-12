---
title: "Gnome-Do closes immediately after launch."
date: 2008-09-13
forum: General Help
---

### Post by Trenchcoat on 2008-09-13
Hi,

I installed and set up gnome-do a moment ago and had it all working. Now, for some reason, I launch it from the Applications menu only to have it turn itself off about a second later. The last thing I did was activate the Evolution Contacts plugin. I'm running Hardy.

---

### Post by AlesUbu123 on 2008-09-13
Hi!

After you run gnome-do, does a new icon appear in the system tray? Can you click it? Does presing Win + X keys make it appear?

If not, you could try to open a terminal and write:
```
gnome-do
```

What is the output of this command in the terminal? Are there any error messages?

---

### Post by Trenchcoat on 2008-09-13
The icon appears briefly. I tried Terminal and got this:

```
** (Do:11981): WARNING **: The following assembly referenced from /home/felix/.local/share/gnome-do/plugins-0.6.0/addins/Do.Evolution.1.2/Evolution.dll could not be loaded:
     Assembly:   evolution-sharp    (assemblyref_index=2)
     Version:    3.0.0.0
     Public Key: 457eed85bd9370df
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/home/felix/.local/share/gnome-do/plugins-0.6.0/addins/Do.Evolution.1.2).


** (Do:11981): WARNING **: Could not load file or assembly 'evolution-sharp, Version=3.0.0.0, Culture=neutral, PublicKeyToken=457eed85bd9370df' or one of its dependencies.
Stacktrace:


Native stacktrace:

	/usr/bin/cli [0x816b1fa]
	/usr/bin/cli [0x807de81]
	[0xb7f21440]

Debug info from gdb:

(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread 0xb7c7f940 (LWP 11981)]
[New Thread 0xb4fffb90 (LWP 11990)]
[New Thread 0xb5d11b90 (LWP 11989)]
[New Thread 0xb7314b90 (LWP 11988)]
[New Thread 0xb7338b90 (LWP 11987)]
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
0xb7f21410 in __kernel_vsyscall ()
  5 Thread 0xb7338b90 (LWP 11987)  0xb7f21410 in __kernel_vsyscall ()
  4 Thread 0xb7314b90 (LWP 11988)  0xb7f21410 in __kernel_vsyscall ()
  3 Thread 0xb5d11b90 (LWP 11989)  0xb7f21410 in __kernel_vsyscall ()
  2 Thread 0xb4fffb90 (LWP 11990)  0xb7e7b86c in g_hash_table_lookup ()
   from /usr/lib/libglib-2.0.so.0
  1 Thread 0xb7c7f940 (LWP 11981)  0xb7f21410 in __kernel_vsyscall ()

Thread 5 (Thread 0xb7338b90 (LWP 11987)):
#0  0xb7f21410 in __kernel_vsyscall ()
#1  0xb7e42196 in nanosleep () from /lib/tls/i686/cmov/libpthread.so.0
#2  0x08105c91 in ?? ()
#3  0xb7e3a4fb in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#4  0xb7d97e5e in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 4 (Thread 0xb7314b90 (LWP 11988)):
#0  0xb7f21410 in __kernel_vsyscall ()
#1  0xb7e3eaa5 in pthread_cond_wait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x081088ff in ?? ()
#3  0x0810b3cd in ?? ()
#4  0x0810b43c in ?? ()
#5  0x0811ba1a in ?? ()
#6  0x080b1c0a in ?? ()
#7  0x080cef04 in ?? ()
#8  0x0811a7c2 in ?? ()
#9  0x081317a5 in ?? ()
#10 0xb7e3a4fb in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#11 0xb7d97e5e in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 3 (Thread 0xb5d11b90 (LWP 11989)):
#0  0xb7f21410 in __kernel_vsyscall ()
#1  0xb7d90881 in select () from /lib/tls/i686/cmov/libc.so.6
#2  0xb7ebf2a4 in g_spawn_sync () from /usr/lib/libglib-2.0.so.0
#3  0xb7ebf66c in g_spawn_command_line_sync () from /usr/lib/libglib-2.0.so.0
#4  0x0816b295 in ?? ()
#5  0x0807de81 in ?? ()
#6  <signal handler called>
Backtrace stopped: previous frame inner to this frame (corrupt stack?)

Thread 2 (Thread 0xb4fffb90 (LWP 11990)):
#0  0xb7e7b86c in g_hash_table_lookup () from /usr/lib/libglib-2.0.so.0
#1  0x080f62ea in mono_method_signature ()
#2  0x0817cc22 in mono_param_get_objects ()
#3  0x080a0f3a in ?? ()
#4  0xb787208f in ?? ()
#5  0xb7872056 in ?? ()
#6  0xb7871d19 in ?? ()
#7  0xb7871b45 in ?? ()
#8  0xb787191c in ?? ()
#9  0xb787111c in ?? ()
#10 0xb78710ad in ?? ()
#11 0xb51f43ab in ?? ()
#12 0xb51f42f7 in ?? ()
#13 0xb51f429d in ?? ()
#14 0xb51f4228 in ?? ()
#15 0xb51f37d2 in ?? ()
#16 0xb51f30a4 in ?? ()
#17 0xb62b909a in ?? ()
#18 0xb62b8fdb in ?? ()
#19 0xb62b8fdb in ?? ()
#20 0xb62b8fdb in ?? ()
#21 0xb62b8e4d in ?? ()
#22 0xb62b8b20 in ?? ()
#23 0xb62f8a39 in ?? ()
#24 0xb62f8844 in ?? ()
#25 0xb5628d54 in ?? ()
#26 0xb655f31e in ?? ()
#27 0x08099ca1 in mono_runtime_class_init ()
#28 0x08158647 in ?? ()
#29 0x0807f936 in ?? ()
#30 0xb7b4c066 in ?? ()
#31 0xb5628399 in ?? ()
#32 0xb5627af8 in ?? ()
#33 0xb56276de in ?? ()
#34 0xb562769d in ?? ()
#35 0xb56274ab in ?? ()
#36 0xb51fcea8 in ?? ()
#37 0xb51fcd6c in ?? ()
#38 0xb51fcca2 in ?? ()
#39 0xb51fbe94 in ?? ()
#40 0xb5d19b42 in ?? ()
#41 0xb7872669 in ?? ()
#42 0x08095ea4 in mono_runtime_delegate_invoke ()
#43 0x080cef6e in ?? ()
#44 0x0811a7c2 in ?? ()
#45 0x081317a5 in ?? ()
#46 0xb7e3a4fb in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#47 0xb7d97e5e in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 1 (Thread 0xb7c7f940 (LWP 11981)):
#0  0xb7f21410 in __kernel_vsyscall ()
#1  0xb7d8dc07 in poll () from /lib/tls/i686/cmov/libc.so.6
#2  0xb7e8c1c6 in ?? () from /usr/lib/libglib-2.0.so.0
#3  0xb7e8c577 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
#4  0xb6d3a264 in gtk_main () from /usr/lib/libgtk-x11-2.0.so.0
#5  0xb5d21796 in ?? ()
#6  0xb5d21760 in ?? ()
#7  0xb786450c in ?? ()
#8  0xb78641c3 in ?? ()
#9  0x0809c63b in mono_runtime_exec_main ()
#10 0x0809c933 in mono_runtime_run_main ()
#11 0x0805acd9 in mono_main ()
#12 0x0805a122 in ?? ()
#13 0xb7cd7450 in __libc_start_main () from /lib/tls/i686/cmov/libc.so.6
#14 0x0805a091 in ?? ()
#0  0xb7f21410 in __kernel_vsyscall ()


=================================================================
Got a SIGSEGV while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries 
used by your application.
=================================================================

Aborted

```

---

### Post by AlesUbu123 on 2008-09-13
What is the output of 'uname -a' in the terminal?

Can you run other programs, such as f-spot or banshee or tomboy normally?

---

### Post by Trenchcoat on 2008-09-13
```
Linux felix-laptop 2.6.24-19-generic #1 SMP Wed Aug 20 22:56:21 UTC 2008 i686 GNU/Linux
```



F-Spot and Tomboy work, Banshee is not installed.

---

### Post by AlesUbu123 on 2008-09-13
> The last thing I did was activate the Evolution Contacts plugin.

If you delete file named 'Do.Evolution,1.2.maddin' in /home/*/.local/share/gnome-do/plugins-0.6.0/addin-db-001/addin-data/global/

where * is your user name, and then try running gnome-do, does it help?

---

### Post by Trenchcoat on 2008-09-13
Like a charm. Thank you!

---

