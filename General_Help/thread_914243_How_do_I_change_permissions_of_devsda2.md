---
title: "How do I change permissions of /dev/sda2 ?"
date: 2008-09-08
forum: General Help
---

### Post by Harry Muscle on 2008-09-08
How do I change permissions of /dev/sda2 ?  I need to be able to access that partition using VirtualBox when I'm logged in.  I know I can add myself to the disk group, but I would rather just give myself permission to only that partition not everything.  I've tried doing a chmod on /dev/sda2 and it works, however, as soon as I reboot the permissions are back to what they were before I changed them.

Thanks,
Harry

---

### Post by bingoUV on 2008-09-08
Do this chmod in /etc/rc.local. It is run at boot time, after all other initialization is done.

---

