---
title: "Mount Windows - Read &amp; Write Access"
date: 2008-08-17
forum: General Help
---

### Post by chinnaraaju on 2008-08-17
Hi,

I like to mount my windows drive with exclusive access **( Read & Write )** in ubuntu.This should happen everytime during **ubuntu boot** process, rather than manual mounting.

Pls provide me commands or relevant setup.

Regards,
Chinna.

---

### Post by dexter on 2008-08-17
We're going to need more info. Can you post the output of
```
sudo fdisk -l
```

---

### Post by chinnaraaju on 2008-08-17
my windows file system is FAT32..
consider my windows D:\ as /sda/dev3 and F:/ as /sda/dev4..

Regards,
Chinna.

---

### Post by dexter on 2008-08-17
Can you lookup the UUID's of them? You can see them by running
```
sudo blkid
```

---

### Post by chinnaraaju on 2008-08-18
Hi,

The result of 'sudo UUID' is as follows...

/dev/sda5: LABEL="Drive-D" UUID="6D11-F452" TYPE="vfat" 
/dev/sda6: LABEL="Drive-E" UUID="BCFC-8667" TYPE="vfat" 
/dev/sda7: LABEL="Drive-F" UUID="6F66-9B47" TYPE="vfat" 

Regards,
Chinna.

---

### Post by sisco311 on 2008-08-18
edit the fstab:
```
gksu gedit /etc/fstab
```and add this lines:
> 
#/dev/sda5 D:
UUID=6D11-F452 /media/**insert-name-here-D **vfat defaults,umask=0002,gid=46 0 0
#/dev/sda7 F:
UUID=6F66-9B47 /media/**insert-name-here-F** vfat defaults,umask=0002,gid=46 0 0save the file and exit.
create the mount points:
```
sudo mkdir /media/[B]insert-name-here-D
[/B]sudo mkdir /media/**insert-name-here-F**
```mount the partitions:
```
sudo mount -a
```

---

