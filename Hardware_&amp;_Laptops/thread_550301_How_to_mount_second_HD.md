---
title: "How to mount second HD?"
date: 2007-09-13
forum: Hardware &amp; Laptops
---

### Post by kealan on 2007-09-13
I installed a slave HD, and created one large ext3 partition.  Now I can't figure out how to mount it.  It is listed as /dev/sdb1.  

Thanks in advance

---

### Post by ntetreau on 2007-09-13
It doesn't come up in nautilus (the file manager?).  If you see an icon somewhere, you can right click on it and then choose "mount".  If not, install gparted and fire it up with 

[CODE]sudo gparted[CODE]

and then choose it in the upper right list.  Right click on the partition and mount it.  There might be options in there to permanently mount it as well.  Hope it helps... if not someone else will!

Nic

---

### Post by logos34 on 2007-09-13
You need to create a mount point (i.e. /media/sdb1) and add an fstab entry so it automounts.
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

### Post by jjalocha on 2007-09-13
It's not clear to me if you formatted your partition? Something like

```
$ sudo mkfs -t ext3 /dev/sdb1
```

---

### Post by steveneddy on 2007-09-13
> **logos34 said:**
> You need to create a mount point (i.e. /media/sdb1) and add an fstab entry so it automounts.
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

This is the best how to on this subject.

aysiu has a great website.

You should read all around his site and you may learn something. I did.

:popcorn:

---

