---
title: "Weird /dev/sdx behaviour"
date: 2008-07-18
forum: General Help
---

### Post by haegl on 2008-07-18
I have 4 pata disks connected to a pci controller. 2 of them are ntfs stripped dynamic volumes. now the problem is that without changing anything, after rebooting they get are mapped in different devices.
i.e. :
```
1st boot
 disk 1 => /dev/sdc
 disk 2 => /dev/sdd
2nd boot
 disk 1 => /dev/sdd
 disk 2 => /dev/sde
```

that inconsistency makes it impossible for me to automate the mounting process. I've also tried to mount them by using uuid but the second disk is not recognized as ntfs and i can't get a uuid...

---

### Post by mcduck on 2008-07-18
> **haegl said:**
> I have 4 pata disks connected to a pci controller. 2 of them are ntfs stripped dynamic volumes. now the problem is that without changing anything, after rebooting they get are mapped in different devices.
i.e. :
```
1st boot
 disk 1 => /dev/sdc
 disk 2 => /dev/sdd
2nd boot
 disk 1 => /dev/sdd
 disk 2 => /dev/sde
```

that inconsistency makes it impossible for me to automate the mounting process. I've also tried to mount them by using uuid but the second disk is not recognized as ntfs and i can't get a uuid...
why you can't get the UUID? what happens when you run "blkid" or "ls -la /dev/disk/by-uuid"?

Also you can label your partitions and use the label in fstab if you, for some strange reason, can't find the UUID.

---

### Post by danwood76 on 2008-07-18
What are you using to stripe the volumes and what disk controller is it?

---

### Post by haegl on 2008-07-18
blkid returns uuid for every disk except those 2. by using vol_id i can get the uuid only for one of them. This also applies to the labels.

```

$ sudo blkid 
/dev/sda1: UUID="7E1C6E9C1C6E4EE9" TYPE="ntfs" LABEL="Media" 
/dev/sdb1: UUID="CA5CCEAC5CCE929D" TYPE="ntfs" LABEL="Backup" 
/dev/sde1: UUID="8898249298248134" TYPE="ntfs" 
/dev/sde2: UUID="f66caa98-6067-4692-933a-fe5a3d94ab89" TYPE="ext3" 
/dev/sde3: TYPE="swap" UUID="0bcb0356-1f25-4875-b9a8-ecefcd7681c8" 
/dev/sde4: UUID="8AA039E9A039DC7F" LABEL="Storage" TYPE="ntfs" 
/dev/mapper/chaos: UUID="FA94FE6A94FE28B1" LABEL="Chaos" TYPE="ntfs" 

$ sudo vol_id /dev/sdc1
ID_FS_USAGE=filesystem
ID_FS_TYPE=ntfs
ID_FS_VERSION=3.1
ID_FS_UUID=FA94FE6A94FE28B1
ID_FS_UUID_ENC=FA94FE6A94FE28B1
ID_FS_LABEL=Chaos
ID_FS_LABEL_ENC=Chaos
ID_FS_LABEL_SAFE=Chaos

$ sudo vol_id /dev/sdd1
/dev/sdd1: unknown volume type

$ ls -l /dev/disk/by-uuid/
total 0
lrwxrwxrwx 1 root root 10 2008-07-18 17:55 0bcb0356-1f25-4875-b9a8-ecefcd7681c8 -> ../../sde3
lrwxrwxrwx 1 root root 10 2008-07-18 17:55 7E1C6E9C1C6E4EE9 -> ../../sda1
lrwxrwxrwx 1 root root 10 2008-07-18 17:55 8898249298248134 -> ../../sde1
lrwxrwxrwx 1 root root 10 2008-07-18 17:55 8AA039E9A039DC7F -> ../../sde4
lrwxrwxrwx 1 root root 10 2008-07-18 17:55 CA5CCEAC5CCE929D -> ../../sdb1
lrwxrwxrwx 1 root root 10 2008-07-18 17:55 f66caa98-6067-4692-933a-fe5a3d94ab89 -> ../../sde2
lrwxrwxrwx 1 root root 10 2008-07-18 17:55 FA94FE6A94FE28B1 -> ../../sdc1


```

here is the configuration table used for dmsetup :
```
# Offset   Size	      Raid     Number     Chunk  1st        Start 2nd	     Start
# into     of the     type     of         size   Device	in	  Device in
# volume   volume              stripes		 device		  device
0	   781432832  striped  2          128    /dev/sdc1  0	  /dev/sdd1  0

```

---

### Post by haegl on 2008-07-18
Controller : [Promise Ultra133 TX2]("http://www.promise.com/product/product_detail_eng.asp?product_id=87")

The volumes are windows (2003 server) software raid-0

---

### Post by danwood76 on 2008-07-18
So which drives/partitions are you trying to automount?

It looks like you have a UUID for each drive and your striped drive is '/dev/mapper/chaos'.

---

### Post by haegl on 2008-07-18
yes, it is created, manually. the problem is to create the /dev/mapper/chaos not to mount it. in the configuration table i've put the device names (/dev/sdc1 and /dev/sdd1) but this only works sometimes as the device names change after rebooting. one solution is to create 2 config tables and let one of them fail...

---

