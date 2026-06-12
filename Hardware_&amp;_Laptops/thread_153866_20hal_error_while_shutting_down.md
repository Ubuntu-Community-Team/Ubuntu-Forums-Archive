---
title: "20hal error while shutting down"
date: 2006-04-01
forum: Hardware &amp; Laptops
---

### Post by blackant on 2006-04-01
I notice this errors while shutting down my computer...

```
Stopping Hardware Abstract Layer:
/etc/dbus-1/event.d/20hal: line 49: /var/run/hal/hald.pid: no such file or directory
Kill usage......
```

It happened after automount and dismount my usb drive.

Eversince, it keeps showing this error message during my shutdown.
Thought everything is still working normal, the message just bothers me...

Anyone can help to solve this problem?
Thank you.

---

### Post by blackant on 2006-04-02
It seems like the problem on exist while I am using 686-smp kernel...

---

### Post by hajk on 2006-04-02
I can confirm something similar: I get the same error during shutdown or rebooting on my desktop running k7-smp kernel; no such problem on my laptop running plain 686 kernel. BTW, the file /var/run/hal/hald.pid IS present before shutting down, so it may get deleted during the shutdown process... this bugs me too.:confused:

---

### Post by Arkoth on 2006-04-29
I have the same problem with the kernel 2.6.12-10-686-smp but without the smp it doesn't ](*,)
help :)

---

