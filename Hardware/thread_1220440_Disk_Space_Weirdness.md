---
title: "Disk Space Weirdness"
date: 2009-07-22
forum: Hardware
---

### Post by alias301 on 2009-07-22
*df -h* shows that I am using a 470GB hard drive with 8.3GB used, but I only have 438GB available.

So am I missing something? Why do I have so much missing disk space??

---

### Post by features on 2009-07-22
Depending on your filesytem (ext, reiser etc), a certain amount is reserved when the filesystem is created.  Ext3, for example, reserves about 5% of the disk.

Also, if you run df as a non-root user, it may not be able to calculate the disk space used by some directories, especially those used by databases to store the DB files. :) To get around this run

```
sudo df -h
```

---

### Post by drs305 on 2009-07-22
Yes, it's the reserved 5%. You can make the reserved percentage smaller or larger with the tune2fs command and switches but unless you are really in need of space it's best to leave it where it is.

---

