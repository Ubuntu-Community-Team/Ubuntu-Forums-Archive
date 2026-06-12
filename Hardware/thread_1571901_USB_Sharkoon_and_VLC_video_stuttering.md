---
title: "USB Sharkoon and VLC video stuttering"
date: 2010-09-10
forum: Hardware
---

### Post by leeezly on 2010-09-10
Hi there

I got this new Sharkoon external USB 2.0 harddrive (ext3, 500GB), which for some reason leads to stuttering in videos (every few minutes) I play from that harddrive using VLC. I do not have this issue with my other external harddrives, so I reckon it must be a hardware issue. But I don't really know where to look for to get this issue solved.

Does anyone know how to find out what might be the problem or how to solve it?

Any help appreciated.

Cheers

---

### Post by viralmeme on 2010-09-10
> **leeezly said:**
> I got this new Sharkoon external USB 2.0 harddrive (ext3, 500GB), which for some reason leads to stuttering in videos ..

Turn off disk polling and use hdparm. Post the output of the following:

$ps -ef > running.processes
--

UID        PID  PPID  C STIME TTY          TIME CMD

root      3766     1  0 14:31 ?        00:00:00 /usr/lib/udisks/udisks-daemon
root      3771  3766  0 14:31 ?        00:00:00 udisks-daemon: polling /dev/sdb
root      3799  3729  0 14:31 ?        00:00:00 hald-addon-storage: polling /dev/sdb (every 2 sec)
root      3808  3729  0 14:31 ?        00:00:00 hald-addon-storage: polling /dev/sr0 (every 2 sec)

---

