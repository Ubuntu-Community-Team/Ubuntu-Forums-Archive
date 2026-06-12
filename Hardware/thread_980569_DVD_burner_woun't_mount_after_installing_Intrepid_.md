---
title: "DVD burner woun't mount after installing Intrepid (permissions problem?)"
date: 2008-11-12
forum: Hardware
---

### Post by rock5505 on 2008-11-12
I'm trying to burn a dvd and it won't let me mount. My fstab looks like this 
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=62864750-5fed-44f9-999a-3440de24fdac /               ext2    defaults,errors=remount-ro,relatime 0       1
# /dev/sda3
UUID=8e394141-719c-4598-b9dd-6699ff9a55e3 /home           ext2    defaults,relatime        0       2
# /dev/sda1
UUID=441bda7f-d2c3-46bb-91c5-886d356f397f none            swap    sw              0       0
/dev/scd0        /media/cdrom0  udf,iso9660 user,noauto,exec,utf8 0 0
/dev/scd1        /media/cdrom1  udf,iso9660 user,noauto,exec,utf8 0 0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
```

Also, when I try to mount manually i get this:


```
mount: block device /dev/scd0 is write-protected, mounting read-only
      mount: /dev/scd0: can't read superblock

```


I am guessing then that it has something to do with my permissions. 
I just don't know how to set it. Thanks for the help in advance.

---

### Post by prshah on 2008-11-13
> **rock5505 said:**
> I'm trying to burn a dvd and it won't let me mount. My fstab looks like this 


Starting from Intrepid, optical devices are no longer needed to be defined in the fstab; they have been moved into the purview of fuse.

So If you just comment out the lines for your dvd devices and reboot, all should be fine.

If it still is a problem, you can just uncomment the lines, and explore other avenues.

---

### Post by rock5505 on 2008-11-13
Thank you. Everything is working fine. I did not know about fuse.

---

