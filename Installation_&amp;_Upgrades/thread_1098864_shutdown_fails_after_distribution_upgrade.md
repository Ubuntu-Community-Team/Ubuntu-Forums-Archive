---
title: "shutdown fails after distribution upgrade"
date: 2009-03-17
forum: Installation &amp; Upgrades
---

### Post by gpsp on 2009-03-17
Hi all,
I just upgraded a server machine from 6.06 LTS to the current version using the do-release-upgrade program (sorry, I'm not quite sure which version that takes me to). The upgrade seemed to go ok, but the machine won't do a restart at the end of the upgrade.

All I'm getting from the command is

root@xyz:/var/log# /sbin/shutdown -r now

Broadcast message from root@xyz
        (/dev/pts/0) at 18:50 ...

The system is going down for reboot NOW!
shutdown: Unable to send message: Connection refused
root@xyz:/var/log#

and then the system doesn't reboot.

It does look like it installed a new kernel, and I'm wondering if I'm missing something with the new kernel install?

---

