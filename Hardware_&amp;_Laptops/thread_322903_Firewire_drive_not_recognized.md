---
title: "Firewire drive not recognized"
date: 2006-12-21
forum: Hardware &amp; Laptops
---

### Post by repyzals on 2006-12-21
Hello,
I'm trying to add an external 300GB firewire disk to my desktop running Ubuntu 6.10 server.

I know the firewire card works under linux because it worked in the past under suse.

The disk and cable are good: I can see the drive under windows xp.

The firewire card seems to be recognized at boot time:

[42949381.190000] ieee1394: Initialized config rom entry `ip1394'
[42949382.650000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[2000000003000934]
[42949395.860000] ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1)
[42949395.860000] ieee1394: sbp2: Try serialize_io=0 for better performance
[42949395.970000] ieee80211_crypt: registered algorithm 'NULL'

When I plug the disk in, nothing happens. No kernel messages. Nothing. If the disk is plugged in at boot time, also no messages in the logs.

I'm not sure how to troubleshoot this. Any suggestions?

---

### Post by repyzals on 2006-12-21
Nevermind, problem solved.

It turns out one of the two firewire connections on the external case is dead.

---

