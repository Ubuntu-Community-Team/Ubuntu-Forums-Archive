---
title: "Mysterious Disk Writes"
date: 2008-10-22
forum: General Help
---

### Post by Jabes on 2008-10-22
Well, mysterious to me anyway.

I've got solid state drives in my laptop.  For the sake of tinkering, I thought i'd try to minimize my writes to the disk and as a side benefit, my SSD might last longer.

This is my fstab file:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=0ac9f2a4-f8bb-4f13-acc7-d99b359bc2f9 /               ext2    noatime,errors=remount-ro 0       1
# /dev/sdb1
UUID=d89fc50e-225f-45a0-bfb2-54c93e82e7dd /home           ext2    noatime        0       2

tmpfs 		/var/log 	tmpfs defaults 0 0
tmpfs 		/tmp 		tmpfs defaults 0 0
tmpfs 		/var/tmp 	tmpfs defaults 0 0
```

In Firefox's about:config file, i've got browser.cache.disk.parent_directory set to /tmp.

I haven't touched my home folder since boot up and yet, here is what iostat gives me:
```
$ iostat -d
Linux 2.6.24-21-eeepc (Eee) 	10/22/2008

Device:            tps   Blk_read/s   Blk_wrtn/s   Blk_read   Blk_wrtn
sda               0.75        36.85         0.14     374500       1416
sdb               1.20         6.11        12.62      62076     128208

```

So my question is, why do i have so many block writes in my /home partition(sdb) versus my root partition(sda)?

---

### Post by dcstar on 2008-10-23
> **Jabes said:**
> Well, mysterious to me anyway.

I've got solid state drives in my laptop.  For the sake of tinkering, I thought i'd try to minimize my writes to the disk and as a side benefit, my SSD might last longer.

This is my fstab file:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=0ac9f2a4-f8bb-4f13-acc7-d99b359bc2f9 /               ext2    noatime,errors=remount-ro 0       1
# /dev/sdb1
UUID=d89fc50e-225f-45a0-bfb2-54c93e82e7dd /home           ext2    noatime        0       2

tmpfs 		/var/log 	tmpfs defaults 0 0
tmpfs 		/tmp 		tmpfs defaults 0 0
tmpfs 		/var/tmp 	tmpfs defaults 0 0
```

In Firefox's about:config file, i've got browser.cache.disk.parent_directory set to /tmp.

I haven't touched my home folder since boot up and yet, here is what iostat gives me:
```
$ iostat -d
Linux 2.6.24-21-eeepc (Eee) 	10/22/2008

Device:            tps   Blk_read/s   Blk_wrtn/s   Blk_read   Blk_wrtn
sda               0.75        36.85         0.14     374500       1416
sdb               1.20         6.11        12.62      62076     128208

```

So my question is, why do i have so many block writes in my /home partition(sdb) versus my root partition(sda)?

Add **nodiratime** and see if things change.

---

### Post by Jabes on 2008-10-23
OK I added nodiratime.
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=0ac9f2a4-f8bb-4f13-acc7-d99b359bc2f9 /               ext2    noatime,nodiratime,errors=remount-ro 0       1
# /dev/sdb1
UUID=d89fc50e-225f-45a0-bfb2-54c93e82e7dd /home           ext2    noatime,nodiratime        0       2

tmpfs 		/var/log 	tmpfs defaults 0 0
tmpfs 		/tmp 		tmpfs defaults 0 0
tmpfs 		/var/tmp 	tmpfs defaults 0 0
```

Rebooted and ran iostat.
```
$ iostat -d
Linux 2.6.24-21-eeepc (Eee) 	10/23/2008

Device:            tps   Blk_read/s   Blk_wrtn/s   Blk_read   Blk_wrtn
sda              10.47       525.88         1.43     329300        896
sdb               2.13        43.00        28.59      26924      17904

```

Looks like no change.  I can't help but think that it has something to do with firefox but i looked through the about:config parameters and nothing popped out at me.

---

