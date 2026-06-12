---
title: "Can't switch to tty"
date: 2009-06-17
forum: Hardware
---

### Post by Halberd on 2009-06-17
The ctrl-alt-f1 (or f2, f3, f4, f5, f6) combination to switch to a different tty is not working.  It does work when I boot into terminal mode, but it does not work when I have X and KDE running.  It might be a KDE problem, because I left a note for myself that it did work when I was running a different window manager (I think Enlightenment).

System details:
Ubuntu 8.04-Server
KDE 3.5
Macbook 1,1 (Intel)
uname -a = Linux ubuntu 2.6.24-21-server #1 SMP Wed Oct 22 00:18:13 UTC 2008 i686 GNU/Linux

---

### Post by Halberd on 2009-06-17
Here's something:  the command "runlevel" tells me I'm in runlevel 2.  According to [http://en.wikipedia.org/wiki/Runlevel#Ubuntu](http://en.wikipedia.org/wiki/Runlevel#Ubuntu), I want to be in runlevel 5 to get display manager with also virtual console logins.  Could this be the problem?  How can I fix it?

ubuntu:/etc/skel halberd$  ps aux | grep getty
root      4760  0.0  0.0   1716   512 tty4     Ss+  Jun16   0:00 /sbin/getty 38400 tty4
root      4761  0.0  0.0   1716   512 tty5     Ss+  Jun16   0:00 /sbin/getty 38400 tty5
root      4765  0.0  0.0   1716   508 tty2     Ss+  Jun16   0:00 /sbin/getty 38400 tty2
root      4766  0.0  0.0   1716   512 tty3     Ss+  Jun16   0:00 /sbin/getty 38400 tty3
root      4768  0.0  0.0   1716   516 tty6     Ss+  Jun16   0:00 /sbin/getty 38400 tty6
root      5719  0.0  0.0   1716   516 tty1     Ss+  Jun16   0:00 /sbin/getty 38400 tty1
halberd  26735  0.0  0.0   3008   756 pts/6    R+   21:05   0:00 grep getty

---

