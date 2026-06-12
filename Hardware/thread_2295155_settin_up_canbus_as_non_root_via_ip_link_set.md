---
title: "settin up canbus as non root via ip link set"
date: 2015-09-16
forum: Hardware
---

### Post by jens22 on 2015-09-16
I am using canbus on ubuntu (mate) via can to usb converter (using socket can).
(can-utils are installed)

As root and via susu everything work fine.

But I want to run it as non root.


Changing the access right for /sbin/ip and ifconfig have not succeeded.
Also adding the user to some additional grounps.

Executing  "ip link set can0 type can bitrate 500000" results in
"RTNETLINK answers: operation not permitted.

What to do? In which group do I have to put the user?

---

