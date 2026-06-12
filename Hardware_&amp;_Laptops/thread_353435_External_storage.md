---
title: "External storage"
date: 2007-02-04
forum: Hardware &amp; Laptops
---

### Post by mk04 on 2007-02-04
I have a 120 GB hard drive that I use for storage, no operating system on it. I formatted it as a ext3 file system, but I can't write to it, only read. I tried a ext2 file system with the same results. I guess my question is, how can i change the permissions to user (me), not root. 

Add'l info, this is my partition table:
EXT3 - 50 GB
Unformatted - 60 GB (not sure what I want to do with this yet, may install another linux OS)

---

### Post by taurus on 2007-02-04
Where do you mount that extra harddrive?  You need to change the ownership of the mount point so you can write to it.  _Assuming_ it's mounted to /media/hdb1 (ext2/ext3) and your login name is john, do

```
sudo chown -R john:john /media/hdb1

```

---

### Post by mk04 on 2007-02-04
I think it worked. Thank you very much!! :)

---

### Post by mk04 on 2007-02-05
Every time I unmount the drive (when I turn my computer off), and reboot the drive I goes back to root-only. Also I have to mount it manually.

---

### Post by mk04 on 2007-02-05
I think the problem was that it wasn't set to boot. Once I unmounted and remounted the drive. It worked good. 

One more weird problem. Under my /media folder I have a partition named Seagate (7.3gb). I have no clue where this partition came from. :confused:

---

