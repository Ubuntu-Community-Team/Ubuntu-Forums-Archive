---
title: "[SOLVED] fstab: automounting ntfs partition"
date: 2008-08-29
forum: General Help
---

### Post by OmnificienT on 2008-08-29
Hello,

I'd say that:
```

/dev/sda5	/media/disk	ntfs-3g rw,auto,exec,utf8 0 	0

```

Should automount my ntfs partition. It does not. What's my mistake?

Thank You.

---

### Post by cdtech on 2008-08-29
Can you post:
sudo fdisk -l

**Update::.**
Using the latest kernel, you wont need to use the ntfs-3g module. Mine is setup as such:
```
# Entry for /dev/sdb1 :
UUID=1D8FD5F25AC0301F /media/Vista ntfs defaults,umask=007,gid=46 0 0
```
I also use the block id in place of the "/dev". You can find that with the command:
```
blkid
```

---

### Post by sisco311 on 2008-08-29
and:
```
sudo blkid
```

---

### Post by OmnificienT on 2008-08-29
Of course:

```

Disk /dev/sda: 500.1 GB, 500107862016 bytes
21 heads, 12 sectors/track, 3876084 cylinders
Units = cylinders of 252 * 512 = 129024 bytes
Disk identifier: 0x6d1bedb4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      416102    52428846    7  HPFS/NTFS
/dev/sda2          416103     3706445   414583218    f  W95 Ext'd (LBA)
/dev/sda5          832205     3706445   362154360    7  HPFS/NTFS
/dev/sda6          416103      816702    50475588   83  Linux
/dev/sda7          816703      832203     1953120   82  Linux swap / Solaris

Partition table entries are not in disk order

```

---

### Post by cdtech on 2008-08-29
Have you created the directory?
sudo mkdir /media/disk

---

### Post by OmnificienT on 2008-08-29
I did create that directory, but:
```

pim@pim-desktop:/media$ sudo mount /dev/sda5
mount: can't find /dev/sda5 in /etc/fstab or /etc/mtab

```

---

### Post by OmnificienT on 2008-08-29
Well I got it to work. I changed the UID in /dev/sda5 again, and now it works.

Thanks for all of your advice.

---

### Post by cdtech on 2008-08-29
cool, glad you got it working...:)

---

