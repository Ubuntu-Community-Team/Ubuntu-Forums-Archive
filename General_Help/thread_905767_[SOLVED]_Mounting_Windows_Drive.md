---
title: "[SOLVED] Mounting Windows Drive"
date: 2008-08-30
forum: General Help
---

### Post by Chronix33 on 2008-08-30
I run Ubuntu from a separate hdd in my computer, and I was wondering if there was a way to have Ubuntu automatically mount my Windows drive. It's not a big hassle, as all I have to do is just click on it in places, but if this could happen automatically every time I log on, that would be great.

---

### Post by fwre01 on 2008-08-30
you need to create a dir e.g /media/sda1 and then add the mount to your /etc/fstab file

```
/dev/sda1   /media/sda1   ntfs-3g   defaults,locale=en_US.utf8   0   0
```

should do it, just replace /dev/sda1 with the partition you wish to mount.

hope this works for ya!!

---

### Post by Chronix33 on 2008-08-30
Alright I'll give it a shot.

---

### Post by Joeb454 on 2008-08-30
You could also try the link in my sig - "HowTo Automount NTFS Drives"

This is the method I use to automount my Vista drive :)

---

