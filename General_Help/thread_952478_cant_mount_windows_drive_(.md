---
title: "cant mount windows drive :("
date: 2008-10-19
forum: General Help
---

### Post by linuxfreak3 on 2008-10-19
cant mount any of my windows drivers.. and i got 4 of them
mount -t ntfs-3g /dev/sdb1/ /media/disk1 -o force
fuse: failed to access mountpoint /media/disk1: Filen eller katalogen finns inte(translation is:File or folder doesnt exsist)

any suggestions what im doing wrong?

---

### Post by sparky-steve on 2008-10-19
Hi

Have you created the directory /media/disk1 ???

```
mkdir /media/disk1
```

the directory must exist before you issue the mount command.

SS

---

### Post by linuxfreak3 on 2008-10-19
lol stupid of me :D

---

### Post by sparky-steve on 2008-10-19
it happens :KS

---

