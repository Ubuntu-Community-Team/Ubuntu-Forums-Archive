---
title: "Access NTSF hard drive in Kubuntu"
date: 2007-02-02
forum: Hardware &amp; Laptops
---

### Post by The Berkut on 2007-02-02
I have three hard drives set on on my computer, the main hard drive has XP on it, the second has Kubuntu, and the third is a storage hard drive thats been formatted in XP. I have this set up on a dual boot configuration, the one that came default when i installed Kubuntu.

I would like to know how i can make the storage drive an interim between the two operating systems, so i can access the files currently saved on the storage while in Kubuntu, and put files on it in Kubuntu that i can access in XP.

Im not very Linux savy though

---

### Post by teaker1s on 2007-02-02
for write look at this thread
[http://www.ubuntuforums.org/showthread.php?t=337970](http://www.ubuntuforums.org/showthread.php?t=337970)

---

### Post by meng on 2007-02-02
Kubuntu can't write to NTFS partitions by default, but it should be able to read them no problem. If you want to take a (small) risk you could try installing ntfs-3g (search the forums for a howto) which will enable reading and writing to NTFS. ntfs-3g is considered experimental whereas ntfs (with read-only access) is considered safe.

---

