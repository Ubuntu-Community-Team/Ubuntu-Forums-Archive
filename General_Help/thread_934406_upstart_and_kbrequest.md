---
title: "upstart and kbrequest"
date: 2008-09-30
forum: General Help
---

### Post by tbonius on 2008-09-30
In previous distros of GNU/Linux I used to have inittab configured with kbrequest spawning an extra TTY with a specific key combination (lets say F12).  Something akin to:

```
kb::kbrequest:/sbin/getty -n -l /bin/bash tty12 115200
```

In newer versions of Ubuntu, SysVinit has been replaced with Upstart.  I have tried configuring a new event in /etc/event.d to do the same thing:

```

#/etc/event.d/tty12
#
# Converted from /etc/inittab entry

start on runlevel 2
start on runlevel 3
start on runlevel 4
start on runlevel 5

stop on shutdown

respawn
kb::kbrequest: /sbin/getty -n -l /bin/bash tty12 115200

```

I can setup the TTY12 entry to respawn using:

```
exec /sbin/getty -n -l /bin/bash tty12 115200
```

But of course this does not use the kbdrequest option to dynamically spawn the shell, and simply just spawns it on boot.  I even tried converting the old inittab entry using migrate-inittab.pl.. but this did not propagate kbrequest in the event entry.  Any helpful hints or tricks in order to configure Upstart to use a kbrequest event?

---

