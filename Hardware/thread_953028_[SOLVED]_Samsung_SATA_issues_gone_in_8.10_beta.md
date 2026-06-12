---
title: "[SOLVED] Samsung SATA issues gone in 8.10 beta"
date: 2008-10-19
forum: Hardware
---

### Post by j_alapeno on 2008-10-19
(Not sure if this is the right place ....) 

I'm [[COLOR="Navy"]building an Ubuntu NAS[/COLOR]]("http://diyubms.blogspot.com/"), and having problems with setting up a RAID1 pair of Samsung HD103UJ 1Tb discs.

On build 8.4.1 I was getting these kernel errors:

[INDENT][SIZE="2"][FONT="Courier New"]syslog.0:Oct 18 18:15:52 anaheim kernel: [ 1387.536520] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
syslog.0:Oct 18 18:15:52 anaheim kernel: [ 1387.536598] ata4.00: cmd 35/00:00:00:bf:02/00:04:00:00:00/e0 tag 0 dma 524288 out
syslog.0:Oct 18 18:15:52 anaheim kernel: [ 1387.536668] ata4.00: status: { DRDY}
syslog.0:Oct 18 18:15:53 anaheim kernel: [ 1388.076037] ata4: soft resetting link
syslog.0:Oct 18 18:15:58 anaheim kernel: [ 1393.271627] ata4: port is slow to respond, please be patient (Status 0xd0)
syslog.0:Oct 18 18:16:03 anaheim kernel: [ 1398.127508] ata4: SRST failed (errno=-16)
syslog.0:Oct 18 18:16:03 anaheim kernel: [ 1398.127565] ata4: soft resetting link
syslog.0:Oct 18 18:16:08 anaheim kernel: [ 1403.323098] ata4: port is slow to respond, please be patient (Status 0xd0)
syslog.0:Oct 18 18:16:13 anaheim kernel: [ 1408.178984] ata4: SRST failed (errno=-16)
syslog.0:Oct 18 18:16:13 anaheim kernel: [ 1408.179039] ata4: soft resetting link
syslog.0:Oct 18 18:16:18 anaheim kernel: [ 1413.374571] ata4: port is slow to respond, please be patient (Status 0xd0)
syslog.0:Oct 18 18:16:48 anaheim kernel: [ 1443.169293] ata4: SRST failed (errno=-16)
syslog.0:Oct 18 18:16:48 anaheim kernel: [ 1443.169348] ata4: soft resetting link
syslog.0:Oct 18 18:16:53 anaheim kernel: [ 1448.185037] ata4: SRST failed (errno=-16)
syslog.0:Oct 18 18:16:53 anaheim kernel: [ 1448.185094] ata4: reset failed, giving up
syslog.0:Oct 18 18:16:53 anaheim kernel: [ 1448.185145] ata4.00: disabled
syslog.0:Oct 18 18:16:53 anaheim kernel: [ 1448.185172] ata4: EH complete[/FONT][/SIZE][/INDENT]

I'm pleased to report that the 8.10 Beta does not seem to have this issue.

Roll on the 30th October !!!! :):):)

---

