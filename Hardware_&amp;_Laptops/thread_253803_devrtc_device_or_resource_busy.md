---
title: "/dev/rtc device or resource busy"
date: 2006-09-08
forum: Hardware &amp; Laptops
---

### Post by DrSpirograph on 2006-09-08
Hi,
I cannot get access to the real time clock on my system, and I suspect it's the cause of serious performance problems with VMWare.

Whenever anything tries to access /dev/rtc (even as root), it gets 
```
/dev/rtc: Device or resource busy
```

However, according to fuser, there is nothing using that file:
```
root@serenity:~# fuser -av /dev/rtc

                     USER        PID ACCESS COMMAND
/dev/rtc:
root@serenity:~#
```

It doesn't seem like everyone is seeing this, but surely I can't be the only person seeing this.

Does anyone know why this is or how I can fix this?

---

### Post by roboknight on 2007-12-31
I am pretty sure I know the cause, but I cannot determine a good solution.  The cause is probably the audio subsystem.  On my system, it hogs the /dev/rtc, thereby not allowing other software to access the rtc device.  The problem is that I have no good solution as I don't really know a good way to get the audio subsystem to release /dev/rtc ... of course if it does, that means choppy audio, but there doesn't seem to be a good way to share /dev/rtc ...

---

