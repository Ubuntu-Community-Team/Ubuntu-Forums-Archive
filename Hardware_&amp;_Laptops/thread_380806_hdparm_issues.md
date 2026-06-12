---
title: "hdparm issues"
date: 2007-03-10
forum: Hardware &amp; Laptops
---

### Post by apollo13 on 2007-03-10
any idea what this does mean:
```
florian@apollo13:~$ sudo hdparm /dev/sr0 

/dev/sr0:
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Inappropriate ioctl for device
florian@apollo13:~$ sudo hdparm /dev/sg0 

/dev/sg0:
 BLKROGET failed: Operation not permitted
 BLKRAGET failed: Operation not permitted
 BLKGETSIZE failed: Operation not permitted
florian@apollo13:~$ sudo hdparm /dev/scd0 

/dev/scd0:
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Inappropriate ioctl for device

```

Thx in advance,
 apollo13

---

