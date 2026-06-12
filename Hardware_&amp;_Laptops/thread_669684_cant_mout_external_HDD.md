---
title: "cant mout external HDD"
date: 2008-01-16
forum: Hardware &amp; Laptops
---

### Post by JermainWijnhard on 2008-01-16
I did the following on my external hdd

```

sudo dd if=/dev/zero of=/dev/sda1 bs=4096

```
[*]Once that finishes, type:
```

sudo mkfs.vfat /dev/sda1

```

So now that its clean i want to use it again, but if i try to mount it, i get "you must specify the filesystem type" im not new, but am quite inexperienced. Can someone give me a push in the right direction? Thank you!

---

### Post by logos34 on 2008-01-16
sudo mount -t vfat /dev/sda1 /<mountpoint>

---

### Post by Plissken@plissken on 2008-01-16
open your system administration and select partion editor choose your what hard disk you want to partition. I have a 160 and a 330GB hard disks and i had to change them to fat32 now I could mount and un-mount both my hard disks with no ease.i hope this will help you it worked for me.

---

### Post by JermainWijnhard on 2008-01-17
> **logos34 said:**
> sudo mount -t vfat /dev/sda1 /<mountpoint>

```
mount: wrong fs type, bad option, bad superblock on /dev/sdb1 /home/jermain/MY\ Book
Missing codepage or other error
In some cases useful info is found in syslog - try
dmsg | tail or so.
```

if i do dmsg | tail i get

```
sdb: Write Protect is off
sdb: Mode Sense: 03 00 00 00
sdb: assuming drive cache: write through
sdb: sdb1
sd 9:0:0:0: Attached sci disk sdb
sd 9:0:0:0: Attached sci generic sg1 type 0
FAT: bogus number of reserved sectors
VFS: Can't find a valid FAT filesystem on dev sdb1.
FAT invalid media value (0xb9)
VFS: Can't find a valid FAT filesystem on dev sdb.
```

I'd really like to get it to work again, all help is welcome!

---

### Post by logos34 on 2008-01-17
is it sda1 or sdb1?

---

