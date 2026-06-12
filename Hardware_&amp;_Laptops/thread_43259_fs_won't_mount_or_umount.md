---
title: "fs won't mount or umount"
date: 2005-06-21
forum: Hardware &amp; Laptops
---

### Post by chewbacca810 on 2005-06-21
alright, I am stumped:

```

anthony@deimos:/usr$ sudo fdisk -l /dev/hdb

Disk /dev/hdb: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        2434    19551073+  83  Linux
anthony@deimos:/usr$ sudo mkdir test
anthony@deimos:/usr$ sudo mount /dev/hdb1 test
mount: /dev/hdb1 already mounted or test busy
anthony@deimos:/usr$ sudo umount /dev/hdb1
umount: /dev/hdb1: not mounted

``` 

Anyone have any clue what's going on or how to fix this?

---

### Post by Zelut on 2005-06-21
This may be too simple but did you verify the /test directory exists & where?  I noticed you didn't use the / in creating the directory... not sure if that'll cause a problem but I always use it.  Maybe take a closer look at where you're trying to mount it... be specific in the path (ie; sudo mount /dev/hdb1 /mnt/test)

---

### Post by chewbacca810 on 2005-06-21
test folder definately exists, second command I issued above.  Made sure anyhow with full path (/mnt/test) and no change, same error.

---

