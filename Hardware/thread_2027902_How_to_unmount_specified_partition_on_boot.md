---
title: "How to unmount specified partition on boot"
date: 2012-07-17
forum: Hardware
---

### Post by mhdbnoimi on 2012-07-17
Hello,

I've an encrypted partition which Ubuntu can't recognize it by default so I want to make it unavailable on boot.

How to unmount specified partition on boot?

PS
I tried this from Ubuntu but it didn't work.

```
sudo umount /dev/sdaX
```

---

### Post by drmrgd on 2012-07-17
Would you mind posting the contents of /etc/fstab?  I think it's just a matter of removing that partitions entry from fstab (or just commenting it out in case you want to access it later).

---

### Post by mhdbnoimi on 2012-07-18
Commenting mount line in fstab fixed the issue.

Thanks:)

---

