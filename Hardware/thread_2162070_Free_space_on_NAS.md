---
title: "Free space on NAS"
date: 2013-07-13
forum: Hardware
---

### Post by tonyMusante on 2013-07-13
Hello,
I have an external harddrive connected to the network and I can't figure out how much free space is left. Is there a terminal command I can use to find out?
TIA

Tony

---

### Post by tgalati4 on 2013-07-13
If you have a permanent mount in /etc/fstab then:

```

cat /etc/fstab
df -h
```

The first command shows what should mount at boot.  The second shows the disk space in human-readable numbers.

---

### Post by tonyMusante on 2013-07-17
Thank you!

---

