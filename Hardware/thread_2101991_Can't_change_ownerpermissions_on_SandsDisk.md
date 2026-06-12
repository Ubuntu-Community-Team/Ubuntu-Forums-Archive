---
title: "Can't change owner/permissions on SandsDisk"
date: 2013-01-06
forum: Hardware
---

### Post by Silvernail on 2013-01-06
I have 3 'SandsDisk' that: I can not remove files: I can not change owner: I can not change permissions.
Can I reformat them?
If so How?  In the 13 years I've been using Linux, I have not reformatted a drive/disk.

Thanks
Dave


```

dave@Dafydd:/media/SANVOL/DCIM/100CANON$ sudo rm *.JPG
rm: cannot remove `IMG_1772.JPG': Read-only file system
rm: cannot remove `IMG_1773.JPG': Read-only file system

```
```

dave@Dafydd:/media/SANVOL/DCIM/100CANON$ ls -l
total 22064
-rw-r--r-- 1 dave dave 2725733 Aug 28 19:16 IMG_1772.JPG
-rw-r--r-- 1 dave dave 2425503 Aug 28 19:17 IMG_1773.JPG
-rw-r--r-- 1 dave dave 2295548 Aug 28 19:17 IMG_1774.JPG

``````

dave@Dafydd:/media/SANVOL/DCIM/100CANON$ sudo chmod 666 *.JPG
chmod: changing permissions of `IMG_1772.JPG': Read-only file system
chmod: changing permissions of `IMG_1773.JPG': Read-only file system
chmod: changing permissions of `IMG_1774.JPG': Read-only file system

``````

dave@Dafydd:/media/SANVOL/DCIM/100CANON$ whoami
dave

``````

dave@Dafydd:/media/SANVOL/DCIM/100CANON$ ls -l
total 22064
-rw-r--r-- 1 dave dave 2725733 Aug 28 19:16 IMG_1772.JPG
-rw-r--r-- 1 dave dave 2425503 Aug 28 19:17 IMG_1773.JPG
-rw-r--r-- 1 dave dave 2295548 Aug 28 19:17 IMG_1774.JPG

```
```

dave@Dafydd:/media/SANVOL/DCIM/100CANON$ sudo chown dave:dave /root
dave@Dafydd:/media/SANVOL/DCIM/100CANON$ ls -l
total 22064
-rw-r--r-- 1 dave dave 2725733 Aug 28 19:16 IMG_1772.JPG
-rw-r--r-- 1 dave dave 2425503 Aug 28 19:17 IMG_1773.JPG
-rw-r--r-- 1 dave dave 2295548 Aug 28 19:17 IMG_1774.JPG

```

---

### Post by tlhIngan on 2013-01-06
This looks like a memory card from a camera.
Is the card's notch in the "read-only" or "lock" position?

---

### Post by Silvernail on 2013-01-07
> **tlhIngan said:**
> This looks like a memory card from a camera.
Is the card's notch in the "read-only" or "lock" position?

Yes they are from my camera and phone. None are notched but all have lock - unlock tabs. I have tried both  positions on all.

---

