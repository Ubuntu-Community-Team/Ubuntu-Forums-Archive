---
title: "[SOLVED] Is it possible to mount an XP partition on boot?"
date: 2007-07-07
forum: Hardware &amp; Laptops
---

### Post by fontenot_1031 on 2007-07-07
Is it possible to mount an XP NTFS hard drive on boot in Feisty?

---

### Post by milton1 on 2007-07-07
Yes, you will need to add a line for the ntfs partition in /etc/fstab. Also, unless you add extra drivers, the partition will mount as read-only by default.

---

### Post by fontenot_1031 on 2007-07-07
Hmm, I think I only need reading abilities.  Thank you for the help!

---

### Post by milton1 on 2007-07-07
You're welcome. If you change your mind about read/write permissions, there are many, many posts about setting up ntfs partitions and the ntfs-3g package. Good luck!

---

### Post by strabes on 2007-07-07
Here are the relevant lines from my /etc/fstab:

> # /dev/sda1
UUID=A4B443E9B443BC94 /media/windows  ntfs    defaults,nls=utf8,umask=007,gid=46 0       1

You could just do it with this though:

```
/dev/sda1 /media/windows ntfs defaults 0 0
```

---

