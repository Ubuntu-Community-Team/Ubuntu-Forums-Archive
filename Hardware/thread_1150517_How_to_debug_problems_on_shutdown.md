---
title: "How to debug problems on shutdown?"
date: 2009-05-06
forum: Hardware
---

### Post by FokkerCharlie on 2009-05-06
Hello!

I've recently upgraded to Jaunty 64 via a clean installation, and generally it's working fine on my Acer 5920G laptop.

However, quite frequently (7/10 times), the computer doesn't want to properly shut down.  The usplash thing happens, then I see a some corruption on the screen, namely lots of fine vertical stripes of various colours.  At this stage, things stop happening.  The only way I can get things going again is with ctrl+alt+del, which reboots the machine!

As there's nothing useful displayed on the screen at the time of the failure, it's not clear to me how to figure out what's causing the problem.  Can someone give me a clue as to where to look so I can debug?

Cheers
Charlie

---

### Post by x33a on 2009-05-06
remove the splash and quiet option from grub menu.lst

This will hopefully verbose the error.

Other than that take a look at the log files.

---

### Post by FokkerCharlie on 2009-05-06
Thanks, x33a

I tried that already, and unfortunately any messages are still obscured by the corrupt screen.  Which log am I looking for for shutdown?

Cheers
Charlie

---

### Post by FokkerCharlie on 2009-05-06
OK, found some interesting stuff in /var/log/messages:

```
May  6 13:55:43 charlie-5920G kernel: [  323.949564] syndaemon[3886]: segfault at f8 ip 00007fe919ecd987 sp 00007fff223d26c0 error 4 in libX11.so.6.2.0[7fe919eb1000+102000]
May  6 13:55:47 charlie-5920G bonobo-activation-server (charlie-4692): could not associate with desktop session: Failed to connect to socket /tmp/dbus-oxTDhIooX3: Connection refused
May  6 13:55:49 charlie-5920G kernel: [  329.791540] nfsd: last server has exited, flushing export cache
May  6 13:55:50 charlie-5920G exiting on signal 15
May  6 13:57:19 charlie-5920G syslogd 1.5.0#5ubuntu3: restart.
```

(I pressed ctrl+alt+del at 13:58:19)

That doesn't look too healthy to me, something to do with syndaemon causing the problem, perhaps?  Grateful to anyone who can make sense of this!

Cheers
Charlie

---

### Post by x33a on 2009-05-06
i can't say anything about this error message, but you can try logging into a tty and first stop gdm, and then do a shutdown, maybe this can yield an error message.

to go to a tty press ctl+alt+f1 or ctrl+alt+f2 ...

1-6 are ttys, ctrl+alt+f7 will get you back on X.

to stop gdm, do this from the tty
```
sudo /etc/init.d/gdm stop
```

---

### Post by FokkerCharlie on 2009-05-06
OK, now the video corruption doesn't seem to be obscuring things- perhaps I didn't disable usplash properly.

Anyway, when I stop GDM, and stop via $sudo halt, I get some messages relating to the EXT-4 filesystem, then:

    Will now halt.

And then nothing.  Ctrl-alt-del gives 'Stopping all Md devices' and a restart.

I also tried the power button from the terminal, and this stopped with 4 EXT4-fs: mballoc messages.

I don't like that!

Ctrl-alt-del restarted the system again.

Any ideas?
Charlie

---

### Post by x33a on 2009-05-06
maybe a problem with the file system.

run fsck on the ubuntu partition.

other than that i am out of ideas.

---

