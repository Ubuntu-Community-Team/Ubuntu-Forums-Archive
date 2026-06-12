---
title: "Ctrl+Alt+[F1/F2/F3] no longer working"
date: 2008-10-10
forum: General Help
---

### Post by jhhoward on 2008-10-10
I have Ubuntu Hardy Heron installed on my laptop. For some reason I can no longer switch to a terminal session by using the Ctrl+Alt+[F1/F2/F3 etc] keyboard shortcut. The keyboard combination used to work but has bizzarely stopped working.

Can anyone point me in the right direction? I read somewhere that this has something to do with the /etc/inittab script (although it was an old post talking about Edgy) but that script does not exist on my system.

---

### Post by geirha on 2008-10-10
Ubuntu now uses upstart. What's the content of /etc/event.d?```
ls -l /etc/event.d/
```

You should have some files named tty{1..6} there for each of the six consoles. If they are there, also output the content of tty1 (which would correspond with Ctrl+Alt+F1)

---

### Post by jhhoward on 2008-10-10
```
ls -l /etc/event.d
total 76
-rw-r--r-- 1 root root 260 2008-04-11 14:49 control-alt-delete
-rw-r--r-- 1 root root 299 2008-04-11 14:49 logd
-rw-r--r-- 1 root root 552 2008-04-11 14:49 rc0
-rw-r--r-- 1 root root 342 2008-04-11 14:49 rc1
-rw-r--r-- 1 root root 403 2008-04-11 14:49 rc2
-rw-r--r-- 1 root root 403 2008-04-11 14:49 rc3
-rw-r--r-- 1 root root 403 2008-04-11 14:49 rc4
-rw-r--r-- 1 root root 403 2008-04-11 14:49 rc5
-rw-r--r-- 1 root root 422 2008-04-11 14:49 rc6
-rw-r--r-- 1 root root 485 2008-04-11 14:49 rc-default
-rw-r--r-- 1 root root 392 2008-04-11 14:49 rcS
-rw-r--r-- 1 root root 575 2008-04-11 14:49 rcS-sulogin
-rw-r--r-- 1 root root 558 2008-04-11 14:49 sulogin
-rw-r--r-- 1 root root 306 2008-04-11 14:49 tty1
-rw-r--r-- 1 root root 300 2008-04-11 14:49 tty2
-rw-r--r-- 1 root root 300 2008-04-11 14:49 tty3
-rw-r--r-- 1 root root 300 2008-04-11 14:49 tty4
-rw-r--r-- 1 root root 300 2008-04-11 14:49 tty5
-rw-r--r-- 1 root root 300 2008-04-11 14:49 tty6
```

```
 cat /etc/event.d/tty1
# tty1 - getty
#
# This service maintains a getty on tty1 from the point the system is
# started until it is shut down again.

start on stopped rc2
start on stopped rc3
start on stopped rc4
start on stopped rc5

stop on runlevel 0
stop on runlevel 1
stop on runlevel 6

respawn
exec /sbin/getty 38400 tty1

```

Anything suspect here?

---

### Post by geirha on 2008-10-10
That pretty much looks like my setup (which is working as expected). Check that the getty process is running ```
ps -ef | grep getty
```

Also, I'm not sure if X applications can override those key combinations, so also try logging out and hit Ctrl+Alt+F1 from the login screen.

---

### Post by jhhoward on 2008-10-10
```

 ps -ef | grep getty
root      4327     1  0 11:30 tty4     00:00:00 /sbin/getty 38400 tty4
root      4328     1  0 11:30 tty5     00:00:00 /sbin/getty 38400 tty5
root      4333     1  0 11:30 tty2     00:00:00 /sbin/getty 38400 tty2
root      4334     1  0 11:30 tty3     00:00:00 /sbin/getty 38400 tty3
root      4338     1  0 11:30 tty6     00:00:00 /sbin/getty 38400 tty6
root      5367     1  0 11:30 tty1     00:00:00 /sbin/getty 38400 tty1
james     8416  5938  0 12:10 pts/0    00:00:00 grep getty

```
Looks like its running...

---

### Post by KeyserSoze93 on 2008-10-10
Do the virtual terminals exist? There is another way to switch terms, by using the chvt command; open a root xterm and type > chvt 1 or whatever F key you would normally use, and see where that gets you.

---

### Post by jhhoward on 2008-10-10
This is interesting.. 

If I open a terminal and do 'sudo chvt 1' it will switch to the virtual terminal. I can then switch between terminals 1-6 by doing ctrl+alt+f[1-6] but once I switch back to the desktop (ctrl+alt+f7) the keyboard shortcut becomes disabled as before.

Is X just ignoring the keyboard shortcuts?

---

### Post by geirha on 2008-10-10
Check System -> Preferences -> Keyboard -> Layouts -> Layout Ootions. Perhaps the Alt or Ctrl keys have been mapped to something else?

Also check /etc/X11/xorg.conf for the same.

---

### Post by jhhoward on 2008-10-23
Nothing suspect in the keyboard settings

---

