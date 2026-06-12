---
title: "Mount Permission Problem"
date: 2008-10-26
forum: General Help
---

### Post by borobudur on 2008-10-26
Hi, I have the problem that I'm trying to synchronize with Unison on a mounted NTFS partition. The system don't let Unison to write on the partition which has this user and permissions: 

```
drwxrwx--- 1 root plugdev
```Unison runs under my user. With other applications like Nautilus it's not a problem under my user to write on the partition. Was wrong here? (perms = 0 is set)

---

### Post by kevstar31 on 2008-10-26
Post your /etc/fstab

---

### Post by borobudur on 2008-10-26
Voilà:
```
#Entry for /dev/hda5 :
UUID=1397F3341CADD101    /media/hda5    ntfs    defaults,umask=007,gid=46    0    1

```

---

### Post by borobudur on 2008-10-31
*** bump ***

---

