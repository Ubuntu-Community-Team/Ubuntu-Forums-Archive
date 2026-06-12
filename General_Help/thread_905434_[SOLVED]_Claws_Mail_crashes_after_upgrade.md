---
title: "[SOLVED] Claws Mail crashes after upgrade"
date: 2008-08-30
forum: General Help
---

### Post by x1a4 on 2008-08-30
Hi,

I just upgraded Claws Mail from the Launchpad repository and now I get a segmentation fault when starting.  

I ran it using the GNU debugger and this is what I got: 
```

$ gdb claws-mail 2>&1 | tee gdb.logs/gdb-claws-mail.txt
GNU gdb 6.8-debian
Copyright (C) 2008 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.  Type "show copying"
and "show warranty" for details.
This GDB was configured as "i486-linux-gnu"...
(gdb) handle SIG33 pass nostop noprint
Signal        Stop	Print	Pass to program	Description
SIG33         No	No	Yes		Real-time event 33
(gdb) set pagination 0
(gdb) run
Starting program: /usr/bin/claws-mail 
[Thread debugging using libthread_db enabled]
[New Thread 0xb6d68720 (LWP 7197)]
[New Thread 0xb67c2b90 (LWP 7200)]

Program received signal SIGSEGV, Segmentation fault.
[Switching to Thread 0xb67c2b90 (LWP 7200)]
mailstream_ssl_context_free (ssl_ctx=0x0) at mailstream_ssl.c:1123
1123	mailstream_ssl.c: No such file or directory.
	in mailstream_ssl.c
(gdb)

```

I did a backtrace and this is what I got:
```

(gdb) backtrace full
#0  mailstream_ssl_context_free (ssl_ctx=0x0) at mailstream_ssl.c:1123
No locals.
#1  0xb763483a in ssl_data_new (fd=18, callback=0, cb_data=<value optimized out>) at mailstream_ssl.c:493
	ssl_data = (struct mailstream_ssl_data *) 0x878d130
	session = (gnutls_session_t) 0x878c520
	cancel = (struct mailstream_cancel *) 0x878d660
	xcred = (gnutls_certificate_credentials_t) 0x878c4c0
	r = <value optimized out>
	ssl_context = (struct mailstream_ssl_context *) 0x0
	cipher_prio = {4, 3, 5, 2, 0}
	kx_prio = {3, 1, 2, 0}
	mac_prio = {3, 2, 0}
	proto_prio = {2, 1, 0}
#2  0xb7634878 in mailstream_low_ssl_open_full (fd=0, starttls=<value optimized out>, callback=0x12, cb_data=0x0) at mailstream_ssl.c:550
	s = (mailstream_low *) 0x0
	ssl_data = <value optimized out>
#3  0xb7634b65 in mailstream_ssl_open_with_callback (fd=18, callback=0, data=0x0) at mailstream_ssl.c:872
	low = <value optimized out>
	s = (mailstream *) 0x0
#4  0xb764b380 in mailimap_ssl_connect_with_callback (f=0x876e618, server=0x8647be0 "imap.googlemail.com", port=993, callback=0, data=0x0) at mailimap_ssl.c:76
	s = 18
	stream = <value optimized out>
#5  0xb764b41c in mailimap_ssl_connect (f=0x876e618, server=0x8647be0 "imap.googlemail.com", port=<value optimized out>) at mailimap_ssl.c:87
No locals.
#6  0x081e8f7d in connect_ssl_run (op=0x876ec80) at imap-thread.c:571
	r = <value optimized out>
	param = (struct connect_param *) 0x12
	result = (struct connect_result *) 0xbff05408
#7  0x08206e62 in thread_run (data=0x8697f40) at etpan-thread-manager.c:340
	op = (struct etpan_thread_op *) 0x876ec80
	thread = <value optimized out>
	r = <value optimized out>
#8  0xb77da4fb in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#9  0xb7598e5e in clone () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
(gdb) info registers
eax            0x0	0
ecx            0x1	1
edx            0x12	18
ebx            0xb76a4978	-1217771144
esp            0xb686d230	0xb686d230
ebp            0xb686d248	0xb686d248
esi            0x0	0
edi            0x878d660	142136928
eip            0xb763457e	0xb763457e <mailstream_ssl_context_free+14>
eflags         0x210286	[ PF SF IF RF ID ]
cs             0x73	115
ss             0x7b	123
ds             0x7b	123
es             0x7b	123
fs             0x0	0
gs             0x33	51
(gdb) thread apply all backtrace

Thread 2 (Thread 0xb686db90 (LWP 7230)):
#0  mailstream_ssl_context_free (ssl_ctx=0x0) at mailstream_ssl.c:1123
#1  0xb763483a in ssl_data_new (fd=18, callback=0, cb_data=<value optimized out>) at mailstream_ssl.c:493
#2  0xb7634878 in mailstream_low_ssl_open_full (fd=0, starttls=<value optimized out>, callback=0x12, cb_data=0x0) at mailstream_ssl.c:550
#3  0xb7634b65 in mailstream_ssl_open_with_callback (fd=18, callback=0, data=0x0) at mailstream_ssl.c:872
#4  0xb764b380 in mailimap_ssl_connect_with_callback (f=0x876e618, server=0x8647be0 "imap.googlemail.com", port=993, callback=0, data=0x0) at mailimap_ssl.c:76
#5  0xb764b41c in mailimap_ssl_connect (f=0x876e618, server=0x8647be0 "imap.googlemail.com", port=<value optimized out>) at mailimap_ssl.c:87
#6  0x081e8f7d in connect_ssl_run (op=0x876ec80) at imap-thread.c:571
#7  0x08206e62 in thread_run (data=0x8697f40) at etpan-thread-manager.c:340
#8  0xb77da4fb in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#9  0xb7598e5e in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 1 (Thread 0xb6e13720 (LWP 7227)):
#0  0xb7fc4410 in __kernel_vsyscall ()
#1  0xb758ec07 in poll () from /lib/tls/i686/cmov/libc.so.6
#2  0xb76e81c6 in g_main_context_iterate (context=0x836ff00, block=1, dispatch=1, self=0x834df30) at /build/buildd/glib2.0-2.16.4/glib/gmain.c:2954
#3  0xb76e874e in IA__g_main_context_iteration (context=0x836ff00, may_block=1) at /build/buildd/glib2.0-2.16.4/glib/gmain.c:2708
#4  0xb7c940d4 in gtk_main_iteration () from /usr/lib/libgtk-x11-2.0.so.0
#5  0x081e4675 in threaded_run (folder=0x867af40, param=0xbff053e8, result=0xbff05408, func=0x81e8f40 <connect_ssl_run>) at imap-thread.c:428
#6  0x081e8d5b in imap_threaded_connect_ssl (folder=0x867af40, server=0x8647be0 "imap.googlemail.com", port=993) at imap-thread.c:606
#7  0x080fbc86 in imap_session_get (folder=0x867af40) at imap.c:1070
#8  0x080fe86c in imap_set_batch (folder=0x867af40, _item=0x867bb30, batch=1) at imap.c:4885
#9  0x080e2341 in folder_item_set_batch (item=0x7, batch=1) at folder.c:4424
#10 0x080e44f9 in folder_item_apply_processing (item=0x867bb30) at folder.c:4235
#11 0x0811b4e3 in initial_processing (item=0x867bb30, data=0x83ad380) at main.c:1955
#12 0x080e25ce in folder_func_to_all_folders_func (node=0x8671f30, data=0x7) at folder.c:1040
#13 0xb76ef195 in g_node_traverse_pre_order (node=0x8671f30, flags=<value optimized out>, func=0x80e25b0 <folder_func_to_all_folders_func>, data=0xbff055a8) at /build/buildd/glib2.0-2.16.4/glib/gnode.c:481
#14 0xb76efca7 in IA__g_node_traverse (root=0x8671f30, order=G_PRE_ORDER, flags=G_TRAVERSE_ALL, depth=-1, func=0x80e25b0 <folder_func_to_all_folders_func>, data=0xbff055a8) at /build/buildd/glib2.0-2.16.4/glib/gnode.c:788
#15 0x080e38e6 in folder_func_to_all_folders (function=0x811b440 <initial_processing>, data=0x83ad380) at folder.c:1057
#16 0x0811d853 in main (argc=Cannot access memory at address 0xfffffdfc
) at main.c:1447
1123	in mailstream_ssl.c
(gdb) quit
The program is running.  Exit anyway? (y or n) n
Not confirmed.
(gdb) quit
$

```

Any ideas?  Thank you.

---

### Post by harvixen on 2008-08-30
hi ..
i also have similar problem. i think it is libetpan 0.55 that got upgraded yesterday.. i have two accounts -  one pop3 other imap..so far i did is i switched off IMAP account and Claws doesn't segfaults on POP3 mail retreival. 
so much for now. i will keep looking what else could be done and i will also try with lower version of libetpan, like 0.52 and see what happens..

i hope there is quick and sound solution.

see my thread:

[http://ubuntuforums.org/showthread.php?t=905337](http://ubuntuforums.org/showthread.php?t=905337)

---

### Post by x1a4 on 2008-08-30
Downgrading libetpan didn't solve if for me, but the Claws Mail repo on Launchpad has just been updated, and it works again.

---

### Post by harvixen on 2008-08-30
i just checked Synaptic. new version has been there and it all works now ..as always. thanx to Claws team - saved my weekend. i suggest you do the same.

best of luck!

harvixen

---

