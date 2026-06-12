---
title: "Mount command ignoring me"
date: 2005-12-28
forum: Hardware &amp; Laptops
---

### Post by blitz666 on 2005-12-28
I had installed Ubuntu 5.10 on my PC, worked good until I crashed it.

This new install has a different video card, and now I cannot mount my NTFS drive for some reason.

The drive is /dev/sda (at least, it should be) and whenever I try to mount, I see the following:

```
sudo mount /dev/sda /xp -t ntfs -o nls=utf8,umask=0222
mount: /dev/sda already mounted or /xp busy
```any way you guys can guide me to fix this?

---

### Post by codejunkie on 2005-12-28
[QUOTE=blitz666]I had installed Ubuntu 5.10 on my PC, worked good until I crashed it.

This new install has a different video card, and now I cannot mount my NTFS drive for some reason.

The drive is /dev/sda (at least, it should be) and whenever I try to mount, I see the following:

```
sudo mount /dev/sda /xp -t ntfs -o nls=utf8,umask=0222
mount: /dev/sda already mounted or /xp busy
```any way you guys can guide me to fix this?[/QUOTE]
in the terminal type ```
sudo fdisk -l
``` this will list the partitions on your drive/drives. im guessing the problem is that partition is actually listed something like sda1 sda2 instead of sda because partitions are usually followed by a number.

---

### Post by blitz666 on 2005-12-28
I appologize... I realized I forgot the 1 right before you posted this...

feel free to ignore this topic now

---

