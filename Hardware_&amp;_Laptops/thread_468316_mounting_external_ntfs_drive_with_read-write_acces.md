---
title: "mounting external ntfs drive with read-write access"
date: 2007-06-08
forum: Hardware &amp; Laptops
---

### Post by rayno on 2007-06-08
i'm trying to mount an external hard drive (Seagate) on my new Kubuntu (Feisty) installation...

my entry in /etc/fstab look like this...

/dev/sda1 /mnt/seagate/ ntfs iocharset=utf8,umask=000 0 0

i was under the impression that umask=000 indicates that the file system should have write access, however, i have no write access when i log in as a user.

i've been searching forums all day and someone suggested changing the permissions on the /mnt/seagate directory.  however, when i try to "chmod", it tells me the file system is read-only.  that's how i know its still mounting read-only

any idea?  (this is my first post!)

-newb

---

### Post by 444 on 2007-06-08
[http://onlyubuntu.blogspot.com/search/label/ntfs-3g-ubuntu-feisty](http://onlyubuntu.blogspot.com/search/label/ntfs-3g-ubuntu-feisty)

---

### Post by merlinus on 2007-06-08
Try installing ntfs-3g from Applications Add/Remove

Also, I do not think you need the trailing slash after seagate.

-merlin

---

### Post by rayno on 2007-06-08
got it!  the correct fstab entry is...

/dev/sda1 /mnt/seagate ntfs-3g defaults 0 0

you must install ntfs-3g first

[www.ntfs-3g.org](www.ntfs-3g.org)

---

