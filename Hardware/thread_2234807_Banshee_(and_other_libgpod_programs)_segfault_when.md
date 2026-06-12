---
title: "Banshee (and other libgpod programs) segfault when iPhone is mounted"
date: 2014-07-17
forum: Hardware
---

### Post by ThatBum on 2014-07-17
Hi. I'm having an issue with putting content on my iPhone. I can mount its filesystem (which was an ordeal in itself, the thing seemed to unpair at random, but I think it's alright now) but if I launch Banshee while the filesystem is mounted, Banshee recognizes the iPhone then crashes shortly after. Otherwise Banshee works fine. I tried it with gtkpod and Rhythmbox as well, same results. I got it to work yesterday but I'm not really sure what I did, as I'm now unable to reproduce it.

Console output follows.

```
justyn@AwesomeNetbook:~$ banshee
[Info  22:50:25.516] Running Banshee 2.6.2: [Ubuntu Trusty Tahr (development branch) (linux-gnu, x86_64) @ 2014-03-25 10:44:19 UTC]
- snip normal output -
[Info  22:50:31.703] AppleDeviceSource is ignoring unmounted volume Documents on Justyn Zachariou&#8217;s iPhone
Stacktrace:




Native stacktrace:


    banshee() [0x4b73d8]
    banshee() [0x50f13b]
    banshee() [0x423d22]
    /lib/x86_64-linux-gnu/libpthread.so.0(+0x10340) [0x7f363db59340]
    /usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0(g_type_check_value_holds+0x3d) [0x7f3638faec3d]
    /usr/lib/x86_64-linux-gnu/libgpod.so.4(+0x207a8) [0x7f360ced47a8]
    /usr/lib/x86_64-linux-gnu/libgpod.so.4(itdb_parse+0x53) [0x7f360ced94d3]
    [0x40e2a2d7]


Debug info from gdb:


Could not attach to process.  If your uid matches the uid of the target
process, check the setting of /proc/sys/kernel/yama/ptrace_scope, or try
again as the root user.  For more details, see /etc/sysctl.d/10-ptrace.conf
ptrace: Operation not permitted.
No threads.


=================================================================
Got a SIGSEGV while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries 
used by your application.
=================================================================


Aborted (core dumped)
justyn@AwesomeNetbook:~$
```

I changed /proc/sys/kernel/yama/ptrace_scope to 0 and ran it again, results of that follow.

```
justyn@AwesomeNetbook:~$ banshee
[Info  23:03:23.016] Running Banshee 2.6.2: [Ubuntu Trusty Tahr (development branch) (linux-gnu, x86_64) @ 2014-03-25 10:44:19 UTC]
- snip normal output -
[Info  23:03:29.481] AppleDeviceSource is ignoring unmounted volume Documents on Justyn Zachariou&#8217;s iPhone
Stacktrace:




Native stacktrace:


    banshee() [0x4b73d8]
    banshee() [0x50f13b]
    banshee() [0x423d22]
    /lib/x86_64-linux-gnu/libpthread.so.0(+0x10340) [0x7fd5de3c6340]
    /usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0(g_type_check_value_holds+0x3d) [0x7fd5d97dac3d]
    /usr/lib/x86_64-linux-gnu/libgpod.so.4(+0x207a8) [0x7fd5ad58b7a8]
    /usr/lib/x86_64-linux-gnu/libgpod.so.4(itdb_parse+0x53) [0x7fd5ad5904d3]
    [0x40644797]


Debug info from gdb:


[New LWP 3767]
[New LWP 3764]
[New LWP 3747]
[New LWP 3746]
[New LWP 3738]
[New LWP 3673]
[New LWP 3672]
[New LWP 3671]
[Thread debugging using libthread_db enabled]
Using host libthread_db library "/lib/x86_64-linux-gnu/libthread_db.so.1".
0x00007fd5de0ddfbd in poll () at ../sysdeps/unix/syscall-template.S:81
81    ../sysdeps/unix/syscall-template.S: No such file or directory.
  Id   Target Id         Frame 
  9    Thread 0x7fd5db31f700 (LWP 3671) "mono" sem_wait () at ../nptl/sysdeps/unix/sysv/linux/x86_64/sem_wait.S:85
  8    Thread 0x7fd5cfeff700 (LWP 3672) "banshee" pthread_cond_wait@@GLIBC_2.3.2 () at ../nptl/sysdeps/unix/sysv/linux/x86_64/pthread_cond_wait.S:185
  7    Thread 0x7fd5c7fff700 (LWP 3673) "gdbus" 0x00007fd5de0ddfbd in poll () at ../sysdeps/unix/syscall-template.S:81
  6    Thread 0x7fd5aee23700 (LWP 3738) "threaded-ml" 0x00007fd5de0ddfbd in poll () at ../sysdeps/unix/syscall-template.S:81
  5    Thread 0x7fd5c4a67700 (LWP 3746) "banshee" 0x00007fd5de3c5b9d in nanosleep () at ../sysdeps/unix/syscall-template.S:81
  4    Thread 0x7fd5a3df9700 (LWP 3747) "banshee" 0x00007fd5de3c53bd in read () at ../sysdeps/unix/syscall-template.S:81
  3    Thread 0x7fd5a3bf8700 (LWP 3764) "banshee" 0x00007fd5de3c56dd in accept () at ../sysdeps/unix/syscall-template.S:81
  2    Thread 0x7fd5adbe3700 (LWP 3767) "banshee" 0x00007fd5de3c5ee9 in __libc_waitpid (pid=pid@entry=3769, stat_loc=stat_loc@entry=0x7fd5cc00731c, options=options@entry=0) at ../sysdeps/unix/sysv/linux/waitpid.c:40
* 1    Thread 0x7fd5deeec7c0 (LWP 3669) "banshee" 0x00007fd5de0ddfbd in poll () at ../sysdeps/unix/syscall-template.S:81


Thread 9 (Thread 0x7fd5db31f700 (LWP 3671)):
#0  sem_wait () at ../nptl/sysdeps/unix/sysv/linux/x86_64/sem_wait.S:85
#1  0x000000000062f667 in mono_sem_wait (sem=sem@entry=0x982440 <finalizer_sem>, alertable=alertable@entry=1) at mono-semaphore.c:119
#2  0x00000000005aba15 in finalizer_thread (unused=unused@entry=0x0) at gc.c:1073
#3  0x000000000058e34b in start_wrapper_internal (data=0x29ecf70) at threads.c:643
#4  start_wrapper (data=0x29ecf70) at threads.c:688
#5  0x000000000062410d in thread_start_routine (args=args@entry=0x29704c8) at wthreads.c:294
#6  0x0000000000633ef5 in inner_start_thread (arg=0x29ece10) at mono-threads-posix.c:49
#7  0x00007fd5de3be182 in start_thread (arg=0x7fd5db31f700) at pthread_create.c:312
#8  0x00007fd5de0eb30d in clone () at ../sysdeps/unix/sysv/linux/x86_64/clone.S:111


Thread 8 (Thread 0x7fd5cfeff700 (LWP 3672)):
#0  pthread_cond_wait@@GLIBC_2.3.2 () at ../nptl/sysdeps/unix/sysv/linux/x86_64/pthread_cond_wait.S:185
#1  0x000000000060da1b in _wapi_handle_timedwait_signal_handle (handle=handle@entry=0x411, timeout=timeout@entry=0x0, alertable=alertable@entry=1, poll=poll@entry=0) at handles.c:1588
#2  0x000000000060da8b in _wapi_handle_wait_signal_handle (handle=handle@entry=0x411, alertable=alertable@entry=1) at handles.c:1533
#3  0x00000000006211cd in WaitForSingleObjectEx (handle=0x411, timeout=timeout@entry=4294967295, alertable=alertable@entry=1) at wait.c:196
#4  0x000000000058d8ef in mono_wait_uninterrupted (thread=thread@entry=0x7fd5db5002e0, multiple=multiple@entry=0, numhandles=numhandles@entry=1, handles=handles@entry=0x7fd5cfefea08, waitall=waitall@entry=0, ms=ms@entry=-1, alertable=1) at threads.c:1455
#5  0x000000000058f6b6 in ves_icall_System_Threading_WaitHandle_WaitOne_internal (this=<optimized out>, handle=0x411, ms=-1, exitContext=<optimized out>) at threads.c:1587
#6  0x000000004153b4e8 in ?? ()
#7  0x00007fd5c8002540 in ?? ()
#8  0x00007fd5dca0cf48 in ?? ()
#9  0x00007fd5c80025c0 in ?? ()
#10 0x00007fd5cfefeac0 in ?? ()
#11 0x00007fd5cfefea40 in ?? ()
#12 0x0000000000000000 in ?? ()


Thread 7 (Thread 0x7fd5c7fff700 (LWP 3673)):
#0  0x00007fd5de0ddfbd in poll () at ../sysdeps/unix/syscall-template.S:81
#1  0x00007fd5dab40fe4 in ?? () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
#2  0x00007fd5dab4130a in g_main_loop_run () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
#3  0x00007fd5d9acfe16 in ?? () from /usr/lib/x86_64-linux-gnu/libgio-2.0.so.0
#4  0x00007fd5dab65f15 in ?? () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
#5  0x00007fd5de3be182 in start_thread (arg=0x7fd5c7fff700) at pthread_create.c:312
#6  0x00007fd5de0eb30d in clone () at ../sysdeps/unix/sysv/linux/x86_64/clone.S:111


Thread 6 (Thread 0x7fd5aee23700 (LWP 3738)):
#0  0x00007fd5de0ddfbd in poll () at ../sysdeps/unix/syscall-template.S:81
#1  0x00007fd5b0474031 in ?? () from /usr/lib/x86_64-linux-gnu/libpulse.so.0
#2  0x00007fd5b046583c in pa_mainloop_poll () from /usr/lib/x86_64-linux-gnu/libpulse.so.0
#3  0x00007fd5b0465ece in pa_mainloop_iterate () from /usr/lib/x86_64-linux-gnu/libpulse.so.0
#4  0x00007fd5b0465f80 in pa_mainloop_run () from /usr/lib/x86_64-linux-gnu/libpulse.so.0
#5  0x00007fd5b0473fe3 in ?? () from /usr/lib/x86_64-linux-gnu/libpulse.so.0
#6  0x00007fd5b0017f08 in ?? () from /usr/lib/x86_64-linux-gnu/pulseaudio/libpulsecommon-4.0.so
#7  0x00007fd5de3be182 in start_thread (arg=0x7fd5aee23700) at pthread_create.c:312
#8  0x00007fd5de0eb30d in clone () at ../sysdeps/unix/sysv/linux/x86_64/clone.S:111


Thread 5 (Thread 0x7fd5c4a67700 (LWP 3746)):
#0  0x00007fd5de3c5b9d in nanosleep () at ../sysdeps/unix/syscall-template.S:81
#1  0x000000000062342b in SleepEx (ms=ms@entry=500, alertable=alertable@entry=1) at wthreads.c:842
#2  0x00000000005914f3 in monitor_thread (unused=unused@entry=0x0) at threadpool.c:779
#3  0x000000000058e34b in start_wrapper_internal (data=0x7fd594031690) at threads.c:643
#4  start_wrapper (data=0x7fd594031690) at threads.c:688
#5  0x000000000062410d in thread_start_routine (args=args@entry=0x297bc60) at wthreads.c:294
#6  0x0000000000633ef5 in inner_start_thread (arg=0x7fd59402b020) at mono-threads-posix.c:49
#7  0x00007fd5de3be182 in start_thread (arg=0x7fd5c4a67700) at pthread_create.c:312
#8  0x00007fd5de0eb30d in clone () at ../sysdeps/unix/sysv/linux/x86_64/clone.S:111


Thread 4 (Thread 0x7fd5a3df9700 (LWP 3747)):
#0  0x00007fd5de3c53bd in read () at ../sysdeps/unix/syscall-template.S:81
#1  0x0000000040377787 in ?? ()
#2  0x00007fd58c002540 in ?? ()
#3  0x0000000000000000 in ?? ()


Thread 3 (Thread 0x7fd5a3bf8700 (LWP 3764)):
#0  0x00007fd5de3c56dd in accept () at ../sysdeps/unix/syscall-template.S:81
#1  0x000000000061b6d5 in _wapi_accept (fd=16, addr=addr@entry=0x0, addrlen=addrlen@entry=0x0) at sockets.c:221
#2  0x0000000000581fa3 in ves_icall_System_Net_Sockets_Socket_Accept_internal (sock=<optimized out>, error=0x7fd5a3bf7ac4, blocking=<optimized out>) at socket-io.c:877
#3  0x00000000413eebfc in ?? ()
#4  0x00007fd590002540 in ?? ()
#5  0x00007fd5dca2d120 in ?? ()
#6  0x00007fd5dca2d120 in ?? ()
#7  0x00007fd5a3bf7af0 in ?? ()
#8  0x00007fd5a3bf7a40 in ?? ()
#9  0x00007fd5dca2d120 in ?? ()
#10 0x00007fd5dc9f75a0 in ?? ()
#11 0x00007fd5dca2d120 in ?? ()
#12 0xffffffffffffffff in ?? ()
#13 0x00000000413ee800 in ?? ()
#14 0x000000000002cf50 in ?? ()
#15 0x0000000000000290 in ?? ()
#16 0x00007fd5a3bf8680 in ?? ()
#17 0x00007fd5dca2d120 in ?? ()
#18 0x00007fd5dc9f75a0 in ?? ()
#19 0x00007fd5dca2cf70 in ?? ()
#20 0x00000000dc9ec628 in ?? ()
#21 0x00007fd5dedf0128 in ?? ()
#22 0x00000000413ee790 in ?? ()
#23 0x00007fd59404adb0 in ?? ()
#24 0x00007fd5dca2d120 in ?? ()
#25 0x00007fd5dc9ec628 in ?? ()
#26 0x00007fd5a3bf7b70 in ?? ()
#27 0x00000000413e9ba8 in ?? ()
#28 0x00007fd5dca381a0 in ?? ()
#29 0x0000000000001f99 in ?? ()
#30 0x00007fd5dca381a0 in ?? ()
#31 0x00007fd5dca381a0 in ?? ()
#32 0x00007fd5a3bf8680 in ?? ()
#33 0x0000000000000000 in ?? ()


Thread 2 (Thread 0x7fd5adbe3700 (LWP 3767)):
#0  0x00007fd5de3c5ee9 in __libc_waitpid (pid=pid@entry=3769, stat_loc=stat_loc@entry=0x7fd5cc00731c, options=options@entry=0) at ../sysdeps/unix/sysv/linux/waitpid.c:40
#1  0x00000000004b7465 in mono_handle_native_sigsegv (signal=signal@entry=11, ctx=ctx@entry=0x7fd5cc007c40) at mini-exceptions.c:2299
#2  0x000000000050f13b in mono_arch_handle_altstack_exception (sigctx=sigctx@entry=0x7fd5cc007c40, fault_addr=<optimized out>, stack_ovf=stack_ovf@entry=0) at exceptions-amd64.c:908
#3  0x0000000000423d22 in mono_sigsegv_signal_handler (_dummy=11, info=0x7fd5cc007d70, context=0x7fd5cc007c40) at mini.c:6769
#4  <signal handler called>
#5  0x00007fd5d97dac3d in g_type_check_value_holds () from /usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0
#6  0x00007fd5ad58b7a8 in ?? () from /usr/lib/x86_64-linux-gnu/libgpod.so.4
#7  0x00007fd5ad5904d3 in itdb_parse () from /usr/lib/x86_64-linux-gnu/libgpod.so.4
#8  0x0000000040644797 in ?? ()
#9  0x00007fd59c090360 in ?? ()
#10 0x00007fd5adbe2d88 in ?? ()
#11 0x00007fd58c002620 in ?? ()
#12 0x00007fd5adbe2aa0 in ?? ()
#13 0x00007fd5adbe26f0 in ?? ()
#14 0x00007fd5adbe2d88 in ?? ()
#15 0x00007fd5dc91de40 in ?? ()
#16 0x00007fd5adbe2d98 in ?? ()
#17 0x00007fd5dcb509f0 in ?? ()
#18 0x0000000040644720 in ?? ()
#19 0x00007fd59c0ce4f0 in ?? ()
#20 0x00000000406446a4 in ?? ()
#21 0x00007fd5dc82cc30 in ?? ()
#22 0x0000000000000000 in ?? ()


Thread 1 (Thread 0x7fd5deeec7c0 (LWP 3669)):
#0  0x00007fd5de0ddfbd in poll () at ../sysdeps/unix/syscall-template.S:81
#1  0x00007fd5dab40fe4 in ?? () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
#2  0x00007fd5dab4130a in g_main_loop_run () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
#3  0x00007fd5d0a84447 in gtk_main () from /usr/lib/x86_64-linux-gnu/libgtk-x11-2.0.so.0
#4  0x0000000041078d05 in ?? ()
#5  0x00007fff90334400 in ?? ()
#6  0x00007fd5dc84c1c0 in ?? ()
#7  0x0000000000000001 in ?? ()
#8  0x00007fff903340f0 in ?? ()
#9  0x00007fff90333ff0 in ?? ()
#10 0x00007fd5dc84c198 in ?? ()
#11 0x0000000000000000 in ?? ()


=================================================================
Got a SIGSEGV while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries 
used by your application.
=================================================================


Aborted (core dumped)
justyn@AwesomeNetbook:~$ 
```

Running it as root makes it unable to recognize the iPhone at all.

The iPhone is a white iPhone 3G 16GB, running iOS 4.2.1. It had jailbroken 4.2.1 but I restored it to vanilla 4.2.1 in an attempt to get it to work. I also tried purging and installing libgpod. The machine is a Eee PC 1015PED running Xubuntu 14.04 Trusty, 64 bit.

Any ideas why this is happening, and how to fix it? Will provide more info if asked.

---

### Post by ThatBum on 2014-07-18
Bump. Still no luck. Note that all the libimobiledevice-utils appear to be working, it must have something specifically to do with libgpod and its ability to manage the iPhone.

EDIT:

After more than a month of intermittent tinkering, I finally figured it out. I felt it was important to put my findings here in case someone had the same problem.

What I did was I deleted the /iTunes_Control/iTunes/ directory from the iPhone's file system. When I reconnected it to Banshee, it rebuilt the entire directory structure and databases and whatnot, as observed in the console output. It seems to be working reliably now with Banshee.

I believe what caused the problem was adding music to the iPhone using Windows software (fubar2000 with iPod Manager component). It must have written to the database in such a way as to have confused libgpod.

EDIT2: Narrowed it down to a xml parsing error with PlayCounts.plist after it's written to by the iPhone. Seems it's been discovered before and nothing's really been done about it, so I doubt I can't change anything. I'll just have to delete that file every time I want to sync.

---

### Post by sp40140 on 2014-07-18
iDevices (iPhone, iPod, iPad) don't work well with Linux. 
Use windows or mac to get this done.

---

### Post by raztus on 2015-03-04
> **ThatBum said:**
> EDIT2: Narrowed it down to a xml parsing error with PlayCounts.plist after it's written to by the iPhone. Seems it's been discovered before and nothing's really been done about it, so I doubt I can't change anything. I'll just have to delete that file every time I want to sync.

You're the man (or woman!) That works for me with my old 2g iPod Touch. Looks like there are a couple of bug reports related to this issue:

[https://bugs.launchpad.net/ubuntu/+source/libgpod/+bug/1381728](https://bugs.launchpad.net/ubuntu/+source/libgpod/+bug/1381728)
[https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/1301257](https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/1301257)

For now, I'll keep deleting PlayCounts.plist.

---

### Post by aeron4 on 2015-05-12
Experiencing the same issue in Xubuntu 15.04 with an old iphone 2g. Deleting the Playcounts.plist file fixed the issue for me.

Thanks for your hard work.

---

