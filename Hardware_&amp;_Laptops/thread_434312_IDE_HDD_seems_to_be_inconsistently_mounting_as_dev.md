---
title: "IDE HDD seems to be inconsistently mounting as /dev/sda &amp; /dev/sdb"
date: 2007-05-05
forum: Hardware &amp; Laptops
---

### Post by kwaanens on 2007-05-05
I have a desktop computer with two hard drives. The mobo is an Asus P5B DLX.
One hard drive is SATA, while the other is IDE. Both ext3. The IDE was put in after original install of Feisty. I think I connected it correctly, because I get no visible errors. But there is one big problem. It is mounted really weird, I see it in gparted as /dev/sda. So my fstab looks like this:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc            proc         defaults                    0  0  
# /dev/sda1
UUID=0a2c21f5-09fb-439a-8239-cd9aaaf5169a  /                ext3         defaults,errors=remount-ro  0  1  
# /dev/sda3
UUID=6714171e-e9d1-49f3-8c00-99996519229b  /media/arkiv     ext3         defaults                    0  2  
# /dev/sda2
UUID=46531a86-b20b-4aa5-bd53-e403e6267305  none             swap         sw                          0  0  
/dev/scd0                                  /media/cdrom0    udf,iso9660  user,noauto                 0  0  
# /dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sdb1                                  /media/backup-1  ext3         defaults 0      0
```

However, it keeps mounting the root file system twice instead. Root file system is mounted both on / and on /media/backup-1

Does anyone have a clue on how I can figure this one out?
I was thinking I might have to find the UUID, but I don't know how to find it.

- Ketil

---

### Post by allenmaher on 2007-05-06
I have been having the same problem, really this is the first thing in the feisty upgrade that is really awful.

I have no idea where to begin with UUID, fstab used to be human readable, these days it is just a mess.
I went into gnome partition editor to discover that the names of the partitions have changed from edgy, but the fstab was not changed accordingly.

---

### Post by lobo235 on 2008-03-26
You can use the **blkid** command to get the UUID for the hard drives connected to your system. Then create/update the entry so it looks like the other entries that are mounted by UUID.

---

