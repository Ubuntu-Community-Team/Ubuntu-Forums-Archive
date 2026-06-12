---
title: "mounting fat volumes at startup"
date: 2009-04-21
forum: Installation &amp; Upgrades
---

### Post by paulopavel@gmail.com on 2009-04-21
What I have to do to mount fat volumes at startup?

---

### Post by lemming465 on 2009-04-23
Include them in /etc/fstab, e.g. if you have a directory /myfatpartition and want /dev/sda5 mounted there```

/dev/sda5  /myfatpartition       vfat    utf8,umask=007,gid=46 0       1
```

---

