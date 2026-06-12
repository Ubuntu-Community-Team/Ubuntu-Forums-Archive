---
title: "f-spot crashes when exporting to folders"
date: 2008-11-07
forum: General Help
---

### Post by senectus on 2008-11-07
I'm trying desperately to archive off a bunch of pictures that I want to share, but f-spot keeps crashing.
I couldn't copy and paste the whole output of the shell session but I hope this helps someone:

```
Saved 19955 bytes
value = f-spot version 0.5.0.3 len = 22
value = 2008:11:08 07:40:43 len = 19
Saved 19955 bytes
value = f-spot version 0.5.0.3 len = 22
value = 2008:11:08 07:40:44 len = 19
Saved 24153 bytes
value = f-spot version 0.5.0.3 len = 22
value = 2008:11:08 07:40:45 len = 19
Stacktrace:


Native stacktrace:

	f-spot [0x817b4ae]
	f-spot [0x807f78b]
	[0xb80f8410]

Debug info from gdb:

(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread 0xb7e376d0 (LWP 24829)]
[New Thread 0xb1a80b90 (LWP 24878)]
[New Thread 0xb1b81b90 (LWP 24876)]
[New Thread 0xb1c82b90 (LWP 24871)]
[New Thread 0xb38fdb90 (LWP 24868)]
[New Thread 0xb36e7b90 (LWP 24838)]
[New Thread 0xb37ecb90 (LWP 24837)]
[New Thread 0xb3db6b90 (LWP 24835)]
[New Thread 0xb73c0b90 (LWP 24831)]
[New Thread 0xb73e4b90 (LWP 24830)]
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
0xb80f8430 in __kernel_vsyscall ()
  10 Thread 0xb73e4b90 (LWP 24830)  0xb80f8430 in __kernel_vsyscall ()
  9 Thread 0xb73c0b90 (LWP 24831)  0xb80f8430 in __kernel_vsyscall ()
  8 Thread 0xb3db6b90 (LWP 24835)  0xb80f8430 in __kernel_vsyscall ()
  7 Thread 0xb37ecb90 (LWP 24837)  0xb80f8430 in __kernel_vsyscall ()
  6 Thread 0xb36e7b90 (LWP 24838)  0xb80f8430 in __kernel_vsyscall ()
  5 Thread 0xb38fdb90 (LWP 24868)  0xb80f8430 in __kernel_vsyscall ()
  4 Thread 0xb1c82b90 (LWP 24871)  0xb80f8430 in __kernel_vsyscall ()
  3 Thread 0xb1b81b90 (LWP 24876)  0xb80f8430 in __kernel_vsyscall ()
  2 Thread 0xb1a80b90 (LWP 24878)  0xb80f8430 in __kernel_vsyscall ()
  1 Thread 0xb7e376d0 (LWP 24829)  0xb80f8430 in __kernel_vsyscall ()

Thread 10 (Thread 0xb73e4b90 (LWP 24830)):
#0  0xb80f8430 in __kernel_vsyscall ()
#1  0xb7ff4906 in nanosleep () from /lib/tls/i686/cmov/libpthread.so.0
#2  0x08110fc8 in ?? ()
#3  0xb7fed50f in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#4  0xb7f447ee in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 9 (Thread 0xb73c0b90 (LWP 24831)):
#0  0xb80f8430 in __kernel_vsyscall ()
#1  0xb7ff1075 in pthread_cond_wait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x081143b7 in ?? ()
#3  0x081169ec in ?? ()
#4  0x08116a2c in ?? ()
#5  0x0812962a in ?? ()
#6  0x080b5c1a in ?? ()
#7  0x080d5f74 in ?? ()
#8  0x081279de in ?? ()
#9  0x0813ff75 in ?? ()
#10 0xb7fed50f in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#11 0xb7f447ee in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 8 (Thread 0xb3db6b90 (LWP 24835)):
#0  0xb80f8430 in __kernel_vsyscall ()
#1  0xb7ff13a2 in pthread_cond_timedwait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x08114368 in ?? ()
#3  0x081169ec in ?? ()
#4  0x08116a2c in ?? ()
#5  0x0812962a in ?? ()
#6  0x080d3013 in ?? ()
#7  0xb4f491fa in ?? ()
#8  0xb4f48feb in ?? ()
#9  0xb4f48f16 in ?? ()
#10 0xb5d818f1 in ?? ()
#11 0x08098c55 in mono_runtime_delegate_invoke ()
#12 0x080d5fdf in ?? ()
#13 0x081279de in ?? ()
#14 0x0813ff75 in ?? ()
#15 0xb7fed50f in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#16 0xb7f447ee in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 7 (Thread 0xb37ecb90 (LWP 24837)):
#0  0xb80f8430 in __kernel_vsyscall ()
#1  0xb7ff13a2 in pthread_cond_timedwait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x08114368 in ?? ()
#3  0x081169ec in ?? ()
#4  0x08116a2c in ?? ()
#5  0x0812962a in ?? ()
#6  0x080d1821 in ?? ()
#7  0xb37f53b2 in ?? ()
#8  0xb37f5296 in ?? ()
#9  0xb37f5188 in ?? ()
#10 0xb5d818f1 in ?? ()
#11 0x08098c55 in mono_runtime_delegate_invoke ()
#12 0x080d5fdf in ?? ()
#13 0x081279de in ?? ()
#14 0x0813ff75 in ?? ()
#15 0xb7fed50f in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#16 0xb7f447ee in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 6 (Thread 0xb36e7b90 (LWP 24838)):
#0  0xb80f8430 in __kernel_vsyscall ()
#1  0xb7ff13a2 in pthread_cond_timedwait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x08114368 in ?? ()
#3  0x081169ec in ?? ()
#4  0x08116a2c in ?? ()
#5  0x0812962a in ?? ()
#6  0x080d1821 in ?? ()
#7  0xb37f53b2 in ?? ()
#8  0xb37f5296 in ?? ()
#9  0xb37f5546 in ?? ()
#10 0xb5d818f1 in ?? ()
#11 0x08098c55 in mono_runtime_delegate_invoke ()
#12 0x080d5fdf in ?? ()
#13 0x081279de in ?? ()
#14 0x0813ff75 in ?? ()
#15 0xb7fed50f in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#16 0xb7f447ee in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 5 (Thread 0xb38fdb90 (LWP 24868)):
#0  0xb80f8430 in __kernel_vsyscall ()
#1  0xb7ff13a2 in pthread_cond_timedwait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x08114368 in ?? ()
#3  0x081169ec in ?? ()
#4  0x08116a2c in ?? ()
#5  0x0812962a in ?? ()
#6  0x080d1821 in ?? ()
#7  0xb37f53b2 in ?? ()
#8  0xb37f5296 in ?? ()
#9  0xb37f5546 in ?? ()
#10 0xb5d818f1 in ?? ()
#11 0x08098c55 in mono_runtime_delegate_invoke ()
#12 0x080d5fdf in ?? ()
#13 0x081279de in ?? ()
#14 0x0813ff75 in ?? ()
#15 0xb7fed50f in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#16 0xb7f447ee in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 4 (Thread 0xb1c82b90 (LWP 24871)):
#0  0xb80f8430 in __kernel_vsyscall ()
#1  0xb7ff13a2 in pthread_cond_timedwait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x08114368 in ?? ()
#3  0x081169ec in ?? ()
#4  0x08116a2c in ?? ()
#5  0x0812962a in ?? ()
#6  0x080d1821 in ?? ()
#7  0xb37f53b2 in ?? ()
#8  0xb37f5296 in ?? ()
#9  0xb37f5546 in ?? ()
#10 0xb5d818f1 in ?? ()
#11 0x08098c55 in mono_runtime_delegate_invoke ()
#12 0x080d5fdf in ?? ()
#13 0x081279de in ?? ()
#14 0x0813ff75 in ?? ()
#15 0xb7fed50f in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#16 0xb7f447ee in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 3 (Thread 0xb1b81b90 (LWP 24876)):
#0  0xb80f8430 in __kernel_vsyscall ()
#1  0xb7f3cc01 in select () from /lib/tls/i686/cmov/libc.so.6
#2  0xb807698b in g_spawn_sync () from /usr/lib/libglib-2.0.so.0
#3  0xb8076d3c in g_spawn_command_line_sync () from /usr/lib/libglib-2.0.so.0
#4  0x0817b565 in ?? ()
#5  0x0807f78b in ?? ()
#6  <signal handler called>
Backtrace stopped: previous frame inner to this frame (corrupt stack?)

Thread 2 (Thread 0xb1a80b90 (LWP 24878)):
#0  0xb80f8430 in __kernel_vsyscall ()
#1  0xb7f39f77 in poll () from /lib/tls/i686/cmov/libc.so.6
#2  0xb8040c32 in ?? () from /usr/lib/libglib-2.0.so.0
#3  0xb80412c2 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
#4  0xb652f8b0 in ?? () from /usr/lib/libORBit-2.so.0
#5  0xb806802f in ?? () from /usr/lib/libglib-2.0.so.0
#6  0xb7fed50f in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#7  0xb7f447ee in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 1 (Thread 0xb7e376d0 (LWP 24829)):
#0  0xb80f8430 in __kernel_vsyscall ()
#1  0xb7f39f77 in poll () from /lib/tls/i686/cmov/libc.so.6
#2  0xb8040c32 in ?? () from /usr/lib/libglib-2.0.so.0
#3  0xb80412c2 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
#4  0xb694c3a9 in gtk_main () from /usr/lib/libgtk-x11-2.0.so.0
#5  0xb218094e in ?? ()
#6  0xb2180918 in ?? ()
#7  0xb2180900 in ?? ()
#8  0xb794bdfd in ?? ()
#9  0xb794a1c4 in ?? ()
#10 0x0809cbb7 in mono_runtime_exec_main ()
#11 0x0809d19b in mono_runtime_run_main ()
#12 0x0805af2e in mono_main ()
#13 0x0805a432 in ?? ()
#14 0xb7e79685 in __libc_start_main () from /lib/tls/i686/cmov/libc.so.6
#15 0x0805a371 in ?? ()
#0  0xb80f8430 in __kernel_vsyscall ()


=================================================================
Got a SIGSEGV while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries 
used by your application.
=================================================================

Aborted

```

---

### Post by ragtag on 2008-11-07
Not much help, but I've had similar problems with it. I was completely unable to import a couple of thousand pictures. Crashed every time. I'm using gThumb now instead, but will be following f-spot in the future to see if it improves.

---

