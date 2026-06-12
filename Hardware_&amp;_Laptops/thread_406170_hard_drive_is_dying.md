---
title: "hard drive is dying"
date: 2007-04-10
forum: Hardware &amp; Laptops
---

### Post by jhenager on 2007-04-10
Is there an equivalent to chkdsk in linux? My hard drive is making noises. It is still under warranty, but it would be great if I could run some kind of diagnostic on it.
Any help from hardware gurus is much appreciated.
jh

---

### Post by dr_d12 on 2007-04-10
To read about fsck type this into your terminal:
```

man fsck

```

You don't want to run it on a mounted volume though.

---

### Post by jhenager on 2007-04-10
> **dr_d12 said:**
> To read about fsck type this into your terminal:
```

man fsck

```

You don't want to run it on a mounted volume though.

fsck says it is fine. The ticking, and hanging says otherwise.
jeff@jeff-desktop:~$ sudo umount /dev/sda1
Password:
jeff@jeff-desktop:~$ sudo fsck /dev/sda1
fsck 1.38 (30-Jun-2005)
e2fsck 1.38 (30-Jun-2005)
/dev/sda1: clean, 158529/24231936 files, 2588612/48462072 blocks

---

### Post by jhenager on 2007-04-10
Just an update - after about three boot attempts, it came back up. I still don't trust it though. I do this for a living, and hard drives are like children - they should be seen but not heard.
:) 
I have backed up my important stuff, but I don't expect that sda1 is long for this world.

---

