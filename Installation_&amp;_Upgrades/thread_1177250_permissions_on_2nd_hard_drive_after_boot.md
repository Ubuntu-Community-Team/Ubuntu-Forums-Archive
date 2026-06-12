---
title: "permissions on 2nd hard drive after boot"
date: 2009-06-03
forum: Installation &amp; Upgrades
---

### Post by ussndmac on 2009-06-03
I added second SATA drive.

I have a mount point /media/datadisk

I have added it to the fstab.

When I boot, the drive is mounted, but only root has write access to it.

If I sudo and umount it, then mount -a, it is again mounted but regular users now have write access.

This is n 9.04, desktop.

What I want is for users to have write access after boot.

---

### Post by theozzlives on 2009-06-03
```
sudo chown yourusername /media/datadisk
```

Then set the permissions so others can read/write

---

### Post by ussndmac on 2009-06-03
I'll try that, but I did a chmod 777 on it as root.

Shouldn't that accomplish the same thing?

---

