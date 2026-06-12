---
title: "UPS problems"
date: 2008-04-26
forum: Hardware
---

### Post by t_ras on 2008-04-26
AMd64 athlon3000+ kubuntu 7.10

I cant make connection with my UPS using NUT.

the service starts OK (or so it seems).

I get in log all the time
```

04/26/2008 02:24:47 PM	terrenisrv1	upsmon[6828]	Poll UPS [myups@localhost] failed - Driver not connected

```
and
```
04/26/2008 02:24:42 PM	terrenisrv1	upsmon[6828]	UPS myups@localhost is unavailable

```

also
```
$ upsc myups@localhost
Error: Driver not connected

```
when trying to connect driver:
```

$ sudo /lib/nut/genericups -x upstype=22 /dev/ttyS1
Network UPS Tools - Generic UPS driver 1.32 (2.0.5)
UPS type: Gamatronic UPSs with alarm interface

```
and also
```

$ sudo /lib/nut/genericups -x upstype=22 /dev/ttyS0
Network UPS Tools - Generic UPS driver 1.32 (2.0.5)
UPS type: Gamatronic UPSs with alarm interface

```

here are my conf files:
ups.conf:
```
 [myups]
 	driver = genericups  upstype=22
	port = auto

```
through I tried directly with ttyS0 and ttyS1. I tried also gamatronic (which is my UPS) but it caused segmentation fault.

upsmon.conf:
```
RUN_AS_USER root
MONITOR myups@localhost 2 monuser Mmmmmm master
```
tried also admin

upsd.conf:
```
ACL all 0.0.0.0/0
ACL localhost 127.0.0.1/32
ACL local <MYIP>
ACCEPT local
ACCEPT localhost
REJECT all

```

upsd.users:
```
[admin]
        password = MMMMMMMMMM
        actions = SET
        instcmds = ALL

[monuser]
        password = MMMMMMMMMMM
        allowfrom = localhost local
        upsmon master

```

Any ideas?

THANKS!

---

### Post by t_ras on 2008-04-26
bump!

---

### Post by t_ras on 2008-04-26
Ok, now reinstalled and  upsc myups@localhost
returns connection refused, though nut user has permissins for every thing I can imagine.
It is part of root, tty and dialout groups.

---

### Post by t_ras on 2008-04-26
bump!

---

