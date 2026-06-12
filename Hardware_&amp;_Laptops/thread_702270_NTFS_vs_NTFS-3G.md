---
title: "NTFS vs NTFS-3G"
date: 2008-02-20
forum: Hardware &amp; Laptops
---

### Post by vikrant82 on 2008-02-20
By default fstab mounts NTFS partitions under 'ntfs' driver. I know i am supposed to use 'ntfs-3g'  to provide more robust support for ntfs read write.

I have been running on hardy, with default ntfs with absolutely no problems or performance hitches. 

I have a feeling that the default ntfs mount on later Ubuntu releases (Gutsy -?) uses ntfs-3g by default.

I am away from my Ubuntu system. Can someone second this ?

---

### Post by julian67 on 2008-02-20
> **vikrant82 said:**
> By default fstab mounts NTFS partitions under 'ntfs' driver. I know i am supposed to use 'ntfs-3g'  to provide more robust support for ntfs read write.

I have been running on hardy, with default ntfs with absolutely no problems or performance hitches. 

I have a feeling that the default ntfs mount on later Ubuntu releases (Gutsy -?) uses ntfs-3g by default.

I am away from my Ubuntu system. Can someone second this ?

yes there is full ntfs read/write built into  Ubuntu Gutsy using ntfs-3g. I don't know if it's now part of the default linux kernel but it's definitely part of Ubuntu Gutsy.

---

