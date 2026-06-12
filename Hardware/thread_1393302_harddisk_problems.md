---
title: "harddisk problems"
date: 2010-01-29
forum: Hardware
---

### Post by wiki10 on 2010-01-29
Hi,

I have a Thinkpad T42 that I used with karmic. But now, I've dropped the thing which was not so healthy for the drive...
So, it has a lot of bad sectors but my guess was to check/repair with a utility (mark bad sectors) and continue.
So I booted with the liveCD, switch to console, do stop GDM and then try to run sudo e2fsck -cc -v -y /dev/sda. It responds with device or resource busy... I cannot find a running process with fuser, the device is NOT mounted.
Please help!

---

### Post by crgutierrez on 2010-04-17
Have you tried System>Admin>gparted?

---

### Post by Drenriza on 2010-04-17
have you tryed booting the system with the live cd and using the following commands

example
```
fsck -t ext2 -fa /dev/hda2 
```

```
badblocks -n
```

---

### Post by davidshere on 2010-04-17
> **wiki10 said:**
> Hi,
 It responds with device or resource busy... I cannot find a running process with fuser, the device is NOT mounted.
Please help!

I just had this exact same problem a few minutes ago.  The solution in this post: [http://ubuntuforums.org/showpost.php?p=5757377&postcount=9](http://ubuntuforums.org/showpost.php?p=5757377&postcount=9)  (to specify the block size) seems to have helped.

```

root@thebone:/# dumpe2fs /dev/sdd1
dumpe2fs 1.40.8 (13-Mar-2008)
...
Block size:               4096
....

root@thebone:/# e2fsck -b 32768 -B 4096 /dev/sdd1
e2fsck 1.40.8 (13-Mar-2008)
/dev/sdd1 was not cleanly unmounted, check forced.
Pass 1: Checking inodes, blocks, and sizes
Inode 23724253, i_size is 282918912, should be 282984448.  Fix<y>? yes

```

---

