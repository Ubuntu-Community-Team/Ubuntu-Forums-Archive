---
title: "Flashdrive is mounted and only root as RW access"
date: 2008-10-08
forum: General Help
---

### Post by malfist on 2008-10-08
Can someone help me? I just got a new flash drive and it is mounted automatically so that only root has read/write access.

This is the appropriate mtab line:
```

/dev/sdf /media/disk vfat rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush 0 0

```

---

