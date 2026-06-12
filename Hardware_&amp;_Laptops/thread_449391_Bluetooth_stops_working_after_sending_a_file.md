---
title: "Bluetooth stops working after sending a file"
date: 2007-05-20
forum: Hardware &amp; Laptops
---

### Post by super breadfish on 2007-05-20
I recently bought a cheap USB Bluetooth dongle so I could send files to and from my Sony Ericsson K750i mobile phone. After installing gnome-bluetooth I can receive files with the dongle perfectly. 
However, when i send files with the Send to - Bluetooth thing, I can only send one file before bluetooth stops working. Whenever I try to send another file, nothing happens, and about a minute later the bug reporting tool pops up with a message about not knowing the program that has crashed, and gives the following error:

```
Memory status: size: 18964480 vsize: 0 resident: 18964480 share: 0 rss: 8175616 rss_rlim: 0
CPU usage: start_time: 1179659671 rtime: 0 utime: 16 stime: 0 cutime:14 cstime: 0 timeout: 2 it_real_value: 0 frequency: 0

Backtrace was generated from '/usr/bin/gnome-obex-send'

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
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
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
[New Thread -1225460048 (LWP 7261)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
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
#1  0xb724b323 in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb7eef1b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
#3  <signal handler called>
#4  0xb736326b in btctl_controller_impl_get_established_rfcomm_connection ()
   from /usr/lib/libbtctl.so.4
#5  0xb73633e7 in btctl_controller_impl_scan_for_service ()
   from /usr/lib/libbtctl.so.4
#6  0xb7360c82 in btctl_controller_scan_for_service ()
   from /usr/lib/libbtctl.so.4
#7  0xb7f41c77 in gnomebt_controller_channels_for_service ()
   from /usr/lib/libgnomebt.so.0
#8  0x08049c57 in ?? ()
#9  0x080a72c0 in ?? ()
#10 0x08060688 in ?? ()
#11 0x00001105 in ?? ()
#12 0x00000004 in ?? ()
#13 0xbff06ad4 in ?? ()
#14 0x0804a3ff in _IO_stdin_used ()
#15 0x0804a500 in _IO_stdin_used ()
#16 0x00000000 in ?? ()

Thread 1 (Thread -1225460048 (LWP 7261)):
#0  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#1  0xb724b323 in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#2  0xb7eef1b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
No symbol table info available.
#3  <signal handler called>
No symbol table info available.
#4  0xb736326b in btctl_controller_impl_get_established_rfcomm_connection ()
   from /usr/lib/libbtctl.so.4
No symbol table info available.
#5  0xb73633e7 in btctl_controller_impl_scan_for_service ()
   from /usr/lib/libbtctl.so.4
No symbol table info available.
#6  0xb7360c82 in btctl_controller_scan_for_service ()
   from /usr/lib/libbtctl.so.4
No symbol table info available.
#7  0xb7f41c77 in gnomebt_controller_channels_for_service ()
   from /usr/lib/libgnomebt.so.0
No symbol table info available.
#8  0x08049c57 in ?? ()
No symbol table info available.
#9  0x080a72c0 in ?? ()
No symbol table info available.
#10 0x08060688 in ?? ()
No symbol table info available.
#11 0x00001105 in ?? ()
No symbol table info available.
#12 0x00000004 in ?? ()
No symbol table info available.
#13 0xbff06ad4 in ?? ()
No symbol table info available.
#14 0x0804a3ff in _IO_stdin_used ()
No symbol table info available.
#15 0x0804a500 in _IO_stdin_used ()
No symbol table info available.
#16 0x00000000 in ?? ()
No symbol table info available.
#0  0xffffe410 in __kernel_vsyscall ()
```

I tried a different bluetooth dongle and had the same problem. I've searched the forum but haven't found anyone else with similar problems but found nothing.

---

### Post by super breadfish on 2007-05-27
Recently upgraded to Feisty....and still have the same problem. When i try to send a second file from computer to phone it hangs, then shows a "Device does not support receiving objects" message, even though i was happy to receive the first.

Once, after unplugging and plugging in the dongle, and restarting the bluetooth services, I could send 3 files after each other....but then I could send anything back to the computer.

---

