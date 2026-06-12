---
title: "Getting logged out every hour"
date: 2008-11-06
forum: General Help
---

### Post by Supa_Fly on 2008-11-06
On Tuesday evening I upgraded to 8.10. I was running 8.04 before that with no issues.
I get logged out on roughly a 50-60 minute cycle (though on the odd occasion that cycle is much shorter), for no apparent reason. I have been running various releases of Ubuntu on this laptop for more than  year now, without this issue & have only seen this since my upgrade.

Here are the various system log messages before I get logged out:
Nov  6 12:21:22 menegroth bonobo-activation-server (des-31650): could not associate with desktop session: Failed to connect to socket /tmp/dbus-sVEf5bLLqv: Connection refused
Nov  6 12:21:30 menegroth pulseaudio[31809]: ltdl-bind-now.c: Failed to find original dlopen loader.
Nov  6 12:21:30 menegroth pulseaudio[31811]: pid.c: Stale PID file, overwriting.
Nov  6 12:21:30 menegroth pulseaudio[31811]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Nov  6 12:21:30 menegroth pulseaudio[31811]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted

Nov  6 12:21:22 menegroth gdmgreeter[31644]: Gtk-WARNING: Unable to locate theme engine in module_path: "ubuntulooks", 
Nov  6 12:21:22 menegroth bonobo-activation-server (des-31650): could not associate with desktop session: Failed to connect to socket /tmp/dbus-sVEf5bLLqv: Connection refused
Nov  6 12:21:30 menegroth pulseaudio[31809]: ltdl-bind-now.c: Failed to find original dlopen loader.
Nov  6 12:21:30 menegroth pulseaudio[31811]: pid.c: Stale PID file, overwriting.
Nov  6 12:21:30 menegroth pulseaudio[31811]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Nov  6 12:21:30 menegroth pulseaudio[31811]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Nov  6 12:21:37 menegroth anacron[31978]: Anacron 2.3 started on 2008-11-06
Nov  6 12:21:37 menegroth anacron[31978]: Normal exit (0 jobs run)
Nov  6 12:22:36 menegroth kernel: [19661.400000] ppdev0: registered pardevice
Nov  6 12:22:36 menegroth python: io/hpmud/pp.c 627: unable to read device-id ret=-1 
Nov  6 12:22:36 menegroth kernel: [19661.448000] ppdev0: unregistered pardevice
Nov  6 12:22:36 menegroth kernel: [19661.836000] ppdev0: registered pardevice
Nov  6 12:22:36 menegroth kernel: [19661.884000] ppdev0: unregistered pardevice
Nov  6 12:22:37 menegroth kernel: [19663.096000] ppdev0: registered pardevice
Nov  6 12:22:37 menegroth hp: io/hpmud/pp.c 627: unable to read device-id ret=-1 
Nov  6 12:22:37 menegroth kernel: [19663.144000] ppdev0: unregistered pardevice
Nov  6 12:30:01 menegroth /USR/SBIN/CRON[32672]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Nov  6 12:40:01 menegroth /USR/SBIN/CRON[1028]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)

Nov  6 12:16:57 menegroth NetworkManager: <info>  (eth1): supplicant connection state change: 4 -> 7 
Nov  6 12:21:17 menegroth gdm[21141]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0 
Nov  6 12:21:19 menegroth acpid: client connected from 31633[0:0] 
Nov  6 12:21:22 menegroth gdmgreeter[31644]: Gtk-WARNING: Unable to locate theme engine in module_path: "ubuntulooks", 

Nov  6 12:50:28 menegroth gdm[1946]: gnome-keyring-daemon: couldn't lookup keyring component setting: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://www.gnome.org/projects/gconf/](http://www.gnome.org/projects/gconf/) for information. (Details -  1: Failed to get connection to session: dbus-launch failed to autolaunch D-Bus session: No protocol specified
Nov  6 12:50:28 menegroth gdm[1946]: Autolaunch error: X11 initialization failed.
Nov  6 12:50:28 menegroth gdm[1946]: )gnome-keyring-daemon: couldn't lookup ssh component setting: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://www.gnome.org/projects/gconf/](http://www.gnome.org/projects/gconf/) for information. (Details -  1: Failed to get connection to session: dbus-launch failed to autolaunch D-Bus session: No protocol specified
Nov  6 12:50:28 menegroth gdm[1946]: Autolaunch error: X11 initialization failed.
Nov  6 12:50:28 menegroth gdm[1946]: )gnome-keyring-daemon: couldn't lookup pkcs11 component setting: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://www.gnome.org/projects/gconf/](http://www.gnome.org/projects/gconf/) for information. (Details -  1: Failed to get connection to session: dbus-launch failed to autolaunch D-Bus session: No protocol specified
Nov  6 12:50:28 menegroth gdm[1946]: Autolaunch error: X11 initialization failed.

---

### Post by scragar on 2008-11-06
> ```
Nov 6 12:21:17 menegroth gdm[21141]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0 
```
By the looks of that you are not being logged out, so much as X(the thing that runs everything graphical) is crashing.

X should make it's own logs in ```
/var/log/Xorg.0.log
```
if you could upload that, and the old version```
/var/log/Xorg.0.log.old
```as attachments I'll take a look, see what I can see.

---

### Post by Supa_Fly on 2008-11-06
Unfortunately those logs exceed the upload limit...

---

### Post by scragar on 2008-11-06
[http://pastebin.com/](http://pastebin.com/) try copy/pasting them there, I should think only the old one would be needed, but I would do both, just in case.

---

### Post by Supa_Fly on 2008-11-06
Righty:
[here it is]("http://pastebin.com/m62611849")
Thanks

---

### Post by scragar on 2008-11-06
OK, this is the back trace, incase you need to talk to anyone else about this problem(saves searching the logs for it again if need be)```
Backtrace:
0: /usr/X11R6/bin/X(xf86SigHandler+0x79) [0x80c3009]
1: [0xffffe420]
2: [0xffffe420]
3: /usr/X11R6/bin/X(ProcSetClipRectangles+0xc1) [0x808acb1]
4: /usr/X11R6/bin/X(Dispatch+0x34f) [0x808c89f]
5: /usr/X11R6/bin/X(main+0x47d) [0x8071d1d]
6: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5) [0xb7b19685]
7: /usr/X11R6/bin/X [0x8071101]
Saw signal 11.  Server aborting.
```

and by the looks of it X itself is the problem. I am going to play around for a while, see if I can find the package responsible for the problem(so you can try reinstalling it), for now though I recomend filing a bug report(and putting a link to this thread in the report and on this thread to the bug report) at bugs.launchpad.net (I'd assume it comes under xorg, but honestly no-one will complain if it's wrong), since it will be much more helpfull than I can be right now.

---

### Post by Supa_Fly on 2008-11-06
Thanks for the input. Here's the link to the [bug report]("https://bugs.launchpad.net/ubuntu/+bug/294662").

---

### Post by Spidge on 2008-11-07
Same problem here - random selection of triggers (though as far as I can se it's always when in use, never spontaneous).

Most recently was whilst flicking up the Applications menu - nothing complex.

bottom of Xorg.0.log.old as follows (2 instances - it crashed again whilst filing report!):
```

Backtrace:
0: /usr/X11R6/bin/X(xf86SigHandler+0x79) [0x80c3009]
1: [0xffffe420]
2: [0xffffe420]
3: /usr/lib/libpixman-1.so.0(pixman_region_subtract+0xb4) [0xb7e3e174]
4: /usr/X11R6/bin/X(miSubtract+0x2b) [0x811cd4b]
5: /usr/lib/xorg/modules//libexa.so [0xb7858368]
6: /usr/lib/xorg/modules//libexa.so [0xb7858b39]
7: /usr/lib/xorg/modules//libexa.so(exaDoMigration+0x64a) [0xb78592fa]
8: /usr/lib/xorg/modules//libexa.so [0xb785a8bb]
9: /usr/lib/xorg/modules//libexa.so(exaComposite+0xb97) [0xb785b8d7]
10: /usr/X11R6/bin/X [0x817720a]
11: /usr/X11R6/bin/X(CompositePicture+0x19a) [0x815fe6a]
12: /usr/X11R6/bin/X [0x8165d35]
13: /usr/X11R6/bin/X [0x8162a55]
14: /usr/X11R6/bin/X(Dispatch+0x34f) [0x808c89f]
15: /usr/X11R6/bin/X(main+0x47d) [0x8071d1d]
16: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5) [0xb7b0e685]
17: /usr/X11R6/bin/X [0x8071101]
Saw signal 11.  Server aborting.
```

```

Backtrace:
0: /usr/X11R6/bin/X(xf86SigHandler+0x79) [0x80c3009]
1: [0xffffe420]
2: [0xffffe420]
3: /usr/lib/libpixman-1.so.0(pixman_region_subtract+0xb4) [0xb7f1f174]
4: /usr/X11R6/bin/X(miSubtract+0x2b) [0x811cd4b]
5: /usr/lib/xorg/modules//libexa.so [0xb7939368]
6: /usr/lib/xorg/modules//libexa.so [0xb7939b39]
7: /usr/lib/xorg/modules//libexa.so(exaDoMigration+0x64a) [0xb793a2fa]
8: /usr/lib/xorg/modules//libexa.so [0xb793b8bb]
9: /usr/lib/xorg/modules//libexa.so(exaComposite+0xb97) [0xb793c8d7]
10: /usr/X11R6/bin/X [0x817720a]
11: /usr/X11R6/bin/X(CompositePicture+0x19a) [0x815fe6a]
12: /usr/X11R6/bin/X [0x8165d35]
13: /usr/X11R6/bin/X [0x8162a55]
14: /usr/X11R6/bin/X(Dispatch+0x34f) [0x808c89f]
15: /usr/X11R6/bin/X(main+0x47d) [0x8071d1d]
16: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5) [0xb7bef685]
17: /usr/X11R6/bin/X [0x8071101]
Saw signal 11.  Server aborting.
```

relevant line from syslog:
```
Nov  7 19:47:51 intrepid-home gdm[9849]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0 
```

Logs attached for reference. Let me know if I'm missing something.

Thanks
Tom

---

