---
title: "Not reading external HDD"
date: 2012-10-03
forum: Hardware
---

### Post by lwalper on 2012-10-03
I've got a WD 1Tb external USB HDD which works as designed as a backup drive on an WinXP system. When I plug the drive into my Ubuntu laptop the drive is not recognized as even being present. Do I need to create a mount point (or some such thing) for the drive to be read?

---

### Post by albandy on 2012-10-03
Open a terminal and type:

tail -f /var/log/syslog

then connect your HD and you will see new lines appearing in the terminal. Copy this new lines and paste it here.

---

### Post by lwalper on 2012-10-03
Maybe it was just a bad hair day. Seems to be working right now??

Thx anyway for your quick reply!

---

