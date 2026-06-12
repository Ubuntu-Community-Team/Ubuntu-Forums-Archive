---
title: "Computer keeps crashing after new RAM install."
date: 2006-12-03
forum: Hardware &amp; Laptops
---

### Post by equal on 2006-12-03
Hey everyone, here's a bit of an annoying situation. I just tried installing a new 1GB 400MHz DDR Kingston RAM stick into my tower, and my computer freaks out! I've got a AMD Athalon 3500+ XP 1.8GHz processor, currently running with a 512MB 400MHz DDR RAM stick, using Ubuntu Edgy.

When I insert the 1GB stick, the bootup screen says I've got 1536MB of RAM installed, so it is reading the stick. Sometimes it crashes during bootup, sometimes I get into the OS before it goes wonky. Here's an error I got from the Bug Buddy at one point:

```
Memory status: size: 60416000 vsize: 0 resident: 60416000 share: 0 rss: 17784832 rss_rlim: 0
CPU usage: start_time: 1165117890 rtime: 0 utime: 117 stime: 0 cutime:110 cstime: 0 timeout: 7 it_real_value: 0 frequency: 0

Backtrace was generated from '/usr/bin/gnome-panel'

(no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
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
[Thread debugging using libthread_db enabled]
[New Thread -1225451856 (LWP 4699)]
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
0xffffe410 in __kernel_vsyscall ()
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb7607323 in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb7f001b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
#3  <signal handler called>
#4  0xb77038af in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
#5  0xb77067df in g_main_context_check () from /usr/lib/libglib-2.0.so.0
#6  0xb7706b89 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
#7  0xb7b05574 in gtk_main () from /usr/lib/libgtk-x11-2.0.so.0
#8  0x08061d8c in main ()

Thread 1 (Thread -1225451856 (LWP 4699)):
#0  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#1  0xb7607323 in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#2  0xb7f001b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
No symbol table info available.
#3  <signal handler called>
No symbol table info available.
#4  0xb77038af in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#5  0xb77067df in g_main_context_check () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#6  0xb7706b89 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#7  0xb7b05574 in gtk_main () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#8  0x08061d8c in main ()
No symbol table info available.
#0  0xffffe410 in __kernel_vsyscall ()

```



I've tried removing the 512MB stick, just running the 1GB, same issue. I'm thinking it's just the stick that's busted, but I thought I'd ask here to see if anyone has any other ideas. It gives me problems on my other drive as well, which has Dapper installed on it. 

I'm wondering though, if the bootup says I've got 1536MB, then it's not an issue with a 1GB stick being too much right?

---

### Post by Sef on 2006-12-03
I belive that the Live CD has a memory test on it as an option....check that and see what comes up.  Need to let it run though a few times.

---

### Post by az on 2006-12-03
> **equal said:**
> 
I'm wondering though, if the bootup says I've got 1536MB, then it's not an issue with a 1GB stick being too much right?

That message is almost useless.  The BIOS is telling you that there is so much ram present, but not that it is working correctly.  If the ram timing is incorrect, or the error checking is wrong, then you may get something like your motherboard trying to write to the ram, but reading fails.

Memtest is a better tool for testing your ram.  It is on the live cd, but it is also installed on your ubuntu system - just enter the grub menu at boot time and pick it.

Also, try installing just the one new stick and running memtest.

---

