---
title: "External USB HDD not detected"
date: 2009-02-22
forum: Hardware
---

### Post by sqadeer on 2009-02-22
When I connect an external WD mypassport USB external hdd to my desktop running 8.10 it is not detected. However the same hdd is detected and is usable on my laptop running 8.04. I am suspecting that the problem is with the hal. Please help.

Thanks in advance.

---

### Post by kahlil88 on 2009-02-22
After trying to connect your hard drive, open a terminal window, type **dmesg | tail** and post the output here.

---

### Post by sqadeer on 2009-02-23
Here is the output from the dmesg:

[  134.549194] type=1503 audit(1235402334.868:6): operation="socket_create" family="ax25" sock_type="dgram" protocol=0 pid=5756 profile="/usr/sbin/cupsd"
[  134.549216] type=1503 audit(1235402334.868:7): operation="socket_create" family="netrom" sock_type="seqpacket" protocol=0 pid=5756 profile="/usr/sbin/cupsd"
[  134.549230] type=1503 audit(1235402334.868:8): operation="socket_create" family="rose" sock_type="dgram" protocol=0 pid=5756 profile="/usr/sbin/cupsd"
[  134.549243] type=1503 audit(1235402334.868:9): operation="socket_create" family="ipx" sock_type="dgram" protocol=0 pid=5756 profile="/usr/sbin/cupsd"
[  134.549257] type=1503 audit(1235402334.868:10): operation="socket_create" family="appletalk" sock_type="dgram" protocol=0 pid=5756 profile="/usr/sbin/cupsd"
[  134.549270] type=1503 audit(1235402334.868:11): operation="socket_create" family="econet" sock_type="dgram" protocol=0 pid=5756 profile="/usr/sbin/cupsd"
[  134.549284] type=1503 audit(1235402334.868:12): operation="socket_create" family="ash" sock_type="dgram" protocol=0 pid=5756 profile="/usr/sbin/cupsd"
[  134.549297] type=1503 audit(1235402334.868:13): operation="socket_create" family="x25" sock_type="seqpacket" protocol=0 pid=5756 profile="/usr/sbin/cupsd"
[  134.549392] type=1503 audit(1235402334.868:14): operation="inode_permission" requested_mask="::r" denied_mask="::r" fsuid=7 name="/proc/5756/net/dev" pid=5756 profile="/usr/sbin/cupsd"
[  137.072294] hub 1-0:1.0: unable to enumerate USB device on port 7

Hope to solve it soon.:(

---

