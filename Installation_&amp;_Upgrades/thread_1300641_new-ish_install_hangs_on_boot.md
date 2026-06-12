---
title: "new-ish install hangs on boot"
date: 2009-10-25
forum: Installation &amp; Upgrades
---

### Post by linuxgrrl on 2009-10-25
hi,
I have a fresh install of Jaunty 64.  It booted properly several times but now hangs when it gets to "starting kernel logging ..."

using a tty I've checked /var/log/boot and /var/log/syslog and dmesg and they do not show any errors.

Since installing the OS I have added mysql, the nvidia drivers, and I mounted some partitions from a large storage disk under /var/music, /var/photos, etc. 

Help!!!  I need to set up mythtv and if I can't boot, obviously 
that plan is not going to happen.  I don't think I can blame the nvidia drivers it seems to hang before getting to the point of booting X.

Thanks in advance for any thoughts...

---

### Post by linuxgrrl on 2009-10-26
Ok, solved my own problem.  In trying to get the permissions for the second sorted out, I had changed permissions on /var ...

Never do that.  Ended up completely reinstalling but everything OK now.

---

