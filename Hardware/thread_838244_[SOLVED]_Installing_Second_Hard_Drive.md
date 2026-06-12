---
title: "[SOLVED] Installing Second Hard Drive"
date: 2008-06-23
forum: Hardware
---

### Post by maustin2 on 2008-06-23
I have installed second hard drive on the server.
It appears under Admin/Disk with all partitions.
Access path is /mnt/sdb. I can only see one partion
under Computer. In Property File Owner and File Group are
Unknown.

Is there a process to make these partions visible and change the
Properties? I know it is something simple, but the time spent
looking could be used installing systems on them.

Thanks for any assistance.

---

### Post by Odrodzona-Sarmacja on 2008-06-23
You should be able to edit your /etc/fstab to mount it with different privileges.

---

