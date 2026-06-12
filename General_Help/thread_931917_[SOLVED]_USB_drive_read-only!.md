---
title: "[SOLVED] USB drive read-only!"
date: 2008-09-27
forum: General Help
---

### Post by josephellengar on 2008-09-27
I have a problem.  I need to save to my usb flash drive, but it is read-only.  What options do I need to add?

The device is /dev/sdb1
(other mounts removed for clarity)

This is my mount output:
/dev/sdb1 on /home/ross/flash type vfat (rw,nodev)
/dev/sda3 on /home/ross/backup type ext2 (rw,nodev)

This is my fstab:

/dev/sdb1 /home/ross/flash vfat users,exec,suid,rw 0 0
/dev/sda3 /home/ross/backup ext2 users,exec,suid,rw 0 0

---

### Post by aysiu on 2008-09-28
Change fstab line to be ```
/dev/sdb1 /home/ross/flash vfat iocharset=utf8,umask=000 0 0
``` Once you've saved those changes, paste this code into the terminal: ```
sudo umount /dev/sdb1
sudo mount -a
```

---

