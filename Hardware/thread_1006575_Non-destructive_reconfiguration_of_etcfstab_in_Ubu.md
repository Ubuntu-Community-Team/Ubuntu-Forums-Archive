---
title: "Non-destructive reconfiguration of /etc/fstab in Ubuntu 8?"
date: 2008-12-09
forum: Hardware
---

### Post by mipetruniak on 2008-12-09
I have a dual-boot environment (XP/Ubuntu 8.x).  I recently removed my ntfs partition only to add it back later.  Furthermore, I added more swap space and allotted more space to my linux partition.

/dev/sda1 - ntfs
/dev/sda2 - linux swap
/dev/sda3 - ext3

I've been getting errors where Ubuntu cannot find the swap space and I am not comfortable editing the /etc/fstab.  In fstab it says that my ext3 is the swap space.

Any thoughts?  Thanks in advance.

---

### Post by taurus on 2008-12-09
When you reinstalled swap, the UUID for that swap partition has changed so you need to edit /etc/fstab to include the new UUID for it.  Open a terminal and post the outputs of these commands.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
sudo blkid
cat /etc/fstab
free
```

---

### Post by mipetruniak on 2008-12-09
sudo fdisk -l
```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7853    63079191    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2            7854        8245     3148740   82  Linux swap / Solaris
/dev/sda3            8246       12161    31455270   83  Linux
Partition 3 does not end on cylinder boundary.
```

sudo blkid
```
/dev/sda1: UUID="75579B717D11E4D2" LABEL="WINDOWSXP" TYPE="ntfs" 
/dev/sda2: TYPE="swap" UUID="a6caa959-bdc2-48fb-90d0-73949626c022" 
/dev/sda3: UUID="52202b85-01b6-4a14-a13c-c673a4797e82" TYPE="ext3" 
```

cat /etc/fstab
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda4
UUID=52202b85-01b6-4a14-a13c-c673a4797e82 /               ext3    relatime,errors=remount-ro 0       1
/dev/sda3       none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sda1  /media/ntfs_1 ntfs  defaults,umask=0 0 0
/dev/sda2       none            swap    sw              0       0

```

free```

             total       used       free     shared    buffers     cached
Mem:       1554468     909528     644940          0      16792     386872
-/+ buffers/cache:     505864    1048604
Swap:      3148732          0    3148732
```


Thanks,
Mike

---

### Post by capn_hector on 2008-12-09
remove the /dev/sda3 line just under the uuid and every thing should be fine.  backup the fstab and keep an ubuntu boot disk around and you have nothing to worry about.

---

### Post by mipetruniak on 2008-12-09
That's it.  Thanks!

---

