---
title: "Hard drives not automounting in Intrepid"
date: 2008-12-29
forum: Hardware
---

### Post by ricemark20 on 2008-12-29
How do I get my hard drives to mount on startup?  
I tried entering the appropriate lines from /proc/mounts in fstab
```
/dev/sdb1 /media/disk-2 vfat rw,nosuid,nodev,uid=1000,fmask=0077,dmask=0077,codepage=cp437,iocharset=iso8859-1,shortname=mixed,utf8,flush 0 0
/dev/sda1 /media/disk-3 fuseblk rw,nosuid,nodev,user_id=0,group_id=0,allow_other,blksize=4096 0 0

```

When I did that, everytime I went to those drives, they gave an error about not having the correct permissions

Also, pysdm is useless

---

