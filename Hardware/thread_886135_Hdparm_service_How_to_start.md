---
title: "Hdparm service? How to start????"
date: 2008-08-10
forum: Hardware
---

### Post by KOTAPAKA on 2008-08-10
I have never seen such a thing. lol I installed hdparm and sysvconfig. I rebooted (just in case) and even then hdparm was not in sysvconfig nor in the serveses menu. How do I start it? In every linux distro it is there and I start the daemon in this way.

---

### Post by linux_tech on 2008-08-10
As a entry in  "/etc/init.d/rc.local", under the "start" section:
Code:
   start)
        /sbin/hdparm -S1 /dev/sdb
        do_start
        ;;

---

