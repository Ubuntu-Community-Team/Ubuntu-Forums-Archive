---
title: "Ubuntu freezes up some seconds"
date: 2010-05-29
forum: Hardware
---

### Post by Rocafort8 on 2010-05-29
I'm having issues with Ubuntu 10.04 on my laptop Dell inspiron 2200. The problem is that the OS freezes every x time about 10 seconds or more.

Searching in the logs I found some strange error messages in syslog similar to this:

```

May 29 07:18:10 guiu-laptop kernel: [10657.736785] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
May 29 07:18:10 guiu-laptop kernel: [10657.736796] sr 0:0:1:0: CDB: Read Capacity(10): 25 00 00 00 00 00 00 00 00 00
May 29 07:18:10 guiu-laptop kernel: [10657.736816] ata1.01: cmd a0/00:00:00:08:00/00:00:00:00:00/b0 tag 0 pio 16392 in
May 29 07:18:10 guiu-laptop kernel: [10657.736818]          res 51/20:03:00:00:00/00:00:00:00:00/b0 Emask 0x1 (device error)
May 29 07:18:10 guiu-laptop kernel: [10657.736823] ata1.01: status: { DRDY ERR }

```

Might it be something related with the hard disk ?

---

### Post by Stigmata13 on 2010-05-29
[http://ubuntuforums.org/showthread.php?t=937872](http://ubuntuforums.org/showthread.php?t=937872)
Seems like they were having the same problem, you might be able to find some info in this thread.

---

