---
title: "How to enable NTFS?"
date: 2005-12-02
forum: Hardware &amp; Laptops
---

### Post by shoaibi on 2005-12-02
Well my question is that how to mount NTFS partitions at the bootup and allow the read and write. And also can we edit the compressed files??? if not then what should i do?Actually there is a very large amount of data in my NTFS partition in compressed form and it will take soo long...........................

---

### Post by aysiu on 2005-12-02
No read-write on NTFS.
Read only.

For read-only... [http://www.ubuntuguide.org/#automountntfs](http://www.ubuntuguide.org/#automountntfs)

---

### Post by shoaibi on 2005-12-02
means either way i have to convert then first to uncompressed form and then change partitions in FAT and atlast enable FAT for read/write at bootup :mad:

---

### Post by aysiu on 2005-12-02
What I did was shrink my NTFS drive to be big enough for Windows XP, then created a huge FAT32 partition in the empty space to share files between XP and Ubuntu--works just fine:

[http://www.ubuntuguide.org/#automountfat](http://www.ubuntuguide.org/#automountfat)

---

