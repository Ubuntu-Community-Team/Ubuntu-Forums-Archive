---
title: "couple of ntfs partitions"
date: 2007-06-17
forum: Hardware &amp; Laptops
---

### Post by vexorian on 2007-06-17
My windows hd configuration is a mess, I got 4 partitions in total:
1, main hard drive one big ntfs partition (C) the rest are ubuntu's partitions and also X which is fat32 so I can exchange stuff between Ubuntu and windows..
2. second hard drive a big ntfs partition D, but also two logical partitions M and V (in that order, sdb1, sdb2, sdb3 )


Feisty installation surprised me when it made C,D and X available to the desktop but it couldn't detect V and M since they are logical, mount does work with them although I would really like it to be done automatically like C, D and X so I wouldn't need sudo to access them, and V is actually my own partition in which I had saved plenty of things, so how do I configure gnome/ubuntu to load them like the other ones?

---

### Post by merlinus on 2007-06-17
Have you installed and configured ntfs-3g?  If not, it is available via Applications/Add Remove.

If yes, then what are the outputs of:

```

sudo fdisk -l
cat /etc/fstab

```

(l is a lowercase L)

-merlin

---

### Post by vexorian on 2007-06-17
hey your post indirectly let me find about:

sudo apt-get install ntfs-config

thanks, not gonna enable write support though, I had my bad experiences with trying to touch those outside windows before, I don't need it anyways so won't take the risk.

---

