---
title: "Software raid after install"
date: 2005-09-11
forum: Hardware &amp; Laptops
---

### Post by Horn on 2005-09-11
I've been trying to create a new linear raid array but I've ran into a problem.

I execute the following command 
```
sudo mdadm --create --verbose /dev/md0 --level=linear --raid-devices=4 /dev/hde /dev/hdf /dev/hdh /dev/hdh
``` 
note: I've done with this and without the partition numbers and the results are the same.

What I get in return instead of a new fancy big disk is this message:

```
mdadm: chunk size defaults to 64K
mdadm: chunk size defaults to 64K
mdadm: ADD_NEW_DISK for /dev/hde failed: Device or resource busy
``` 


If I run the command a second time I get this instead
```

mdadm: chunk size defaults to 64K
mdadm: /dev/hde1 appears to contain an ext2fs file system
    size=40017880K  mtime=Sun Sep 11 00:21:52 2005
Continue creating array? yes
mdadm: SET_ARRAY_INFO failed for /dev/md0: Device or resource busy
```


All of the harddrives have a single linux raid partition(fd in cfdisk) on them.  I'm using the 2.6.10-5-686 ubuntu kernel.  I'm sure theres something stupid I'm forgetting ](*,) .  Any ideas?

---

### Post by Horn on 2005-09-11
Anyone have any ideas?

---

