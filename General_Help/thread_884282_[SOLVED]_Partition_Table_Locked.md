---
title: "[SOLVED] Partition Table Locked?"
date: 2008-08-08
forum: General Help
---

### Post by Gannon8 on 2008-08-08
I want to format my 1GB SD card so I can use it to boot Linux on the Wii (They found a way :) ). I need to format it with one fat32 partition and one ext3 partition. When I try and format it though, I get an error:
```
***@***:~$ sudo mkfs.ext3 /dev/sde2
mke2fs 1.40.8 (13-Mar-2008)
/dev/sde2: Read-only file system while setting up superblock
```
Even forcing, doubly forcing, GParted nor sfdisk work either. sfdisk error:
```
***@***:~$ sudo sfdisk /dev/sde -f
/dev/sde: Read-only file system

sfdisk: cannot open /dev/sde read-write

```

GParted cannot make a new disklabel. Any help on how to totally shred the partition table and make a new one?

---

### Post by Gannon8 on 2008-08-08
BTW, I can mount the partition as read-only, and I can see some files that I previously had on there.

---

### Post by Gannon8 on 2008-08-08
Anyone?

---

### Post by Crafty Kisses on 2008-08-08
> **Gannon8 said:**
> Anyone?

Post the following:
```
fstab
```

---

### Post by falcon61102 on 2008-08-08
Also, have you tried starting gparted through the terminal using sudo instead of the menus?

---

### Post by Crafty Kisses on 2008-08-09
> **falcon61102 said:**
> Also, have you tried starting gparted through the terminal using sudo instead of the menus?

Yeah you may want to try the following:
```
gksu gparted
```

---

