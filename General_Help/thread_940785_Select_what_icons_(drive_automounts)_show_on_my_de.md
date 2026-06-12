---
title: "Select what icons (drive automounts) show on my desktop ???"
date: 2008-10-07
forum: General Help
---

### Post by vikrant_me on 2008-10-07
[LIST]
[*]How do i disable some of the partitioons automounted from showing on my desktop???
[*]Remember i just dont want some of them not to show, nothing to do with having them either automount or not.
[/LIST]

---

### Post by drs305 on 2008-10-07
One way to do it is to change the mountpoint from /media/xxxxx to /mnt/xxxxx
I don't know of a way to selectively hide partitions on the desktop. Partitions mounted in /media traditionally show up on the Desktop while those mounted in /mnt do not.

To make the change, you will need to create the folders in /mnt, change the ownership of these folders to yourself, and change the mount points in fstab.

---

### Post by vikrant_me on 2009-03-16
> **drs305 said:**
> One way to do it is to change the mountpoint from /media/xxxxx to /mnt/xxxxx
I don't know of a way to selectively hide partitions on the desktop. Partitions mounted in /media traditionally show up on the Desktop while those mounted in /mnt do not.

To make the change, you will need to create the folders in /mnt, change the ownership of these folders to yourself, and change the mount points in fstab.


I will give this a shot, is there another way besides this ?

---

