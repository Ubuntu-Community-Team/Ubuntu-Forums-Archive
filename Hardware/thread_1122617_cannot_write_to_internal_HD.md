---
title: "cannot write to internal HD"
date: 2009-04-11
forum: Hardware
---

### Post by stans on 2009-04-11
OK - after quite a bit of searching I am now ready to ask for help. Installed two new internal drives and cannot write to them from various applications. 

Can someone direct me to a 'how to install a internal HD' thread ?

Thanks.

---

### Post by taurus on 2009-04-11
What filesystem are those two internal drives?

Open a terminal and post the outputs of these commands, running one at a time.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
sudo blkid
cat /etc/fstab
df -h
```

---

### Post by labinnsw on 2009-04-11
Are you able to read the drives and if so, have you checked the permissions?

---

### Post by stans on 2009-04-11
Thank you for the replies. Yes, checked permissions and that is what is baffling me. As ROOT I can do a MKDIR. 

Here's the output from the commands. A learning experience in itself !



Disk /dev/sda: 300.0 GB, 300069052416 bytes

255 heads, 63 sectors/track, 36481 cylinders

Units = cylinders of 16065 * 512 = 8225280 bytes

Disk identifier: 0x00005028



   Device Boot      Start         End      Blocks   Id  System

/dev/sda1   *           1       35725   286961031   83  Linux

/dev/sda2           35726       36481     6072570    5  Extended

/dev/sda5           35726       36481     6072538+  82  Linux swap / Solaris



Disk /dev/sdb: 80.0 GB, 80000000000 bytes

255 heads, 63 sectors/track, 9726 cylinders

Units = cylinders of 16065 * 512 = 8225280 bytes

Disk identifier: 0x00005028



   Device Boot      Start         End      Blocks   Id  System

/dev/sdb1   *           1        9726    78124063+  83  Linux



Disk /dev/sdc: 500.1 GB, 500107862016 bytes

255 heads, 63 sectors/track, 60801 cylinders

Units = cylinders of 16065 * 512 = 8225280 bytes

Disk identifier: 0x00048cbc



   Device Boot      Start         End      Blocks   Id  System

/dev/sdc1               1       60801   488384001   83  Linux


stan@stan-desktop:/$ sudo blkid

/dev/sda1: UUID="910440c5-7bd2-48e5-a885-85cf80f50c8b" TYPE="ext3" 

/dev/sda5: TYPE="swap" UUID="8a462438-77e4-4138-86f1-3810c73931f2" 

/dev/sdb1: UUID="e35501d9-476a-42ac-aa90-e6cf855dda5f" SEC_TYPE="ext2" TYPE="ext3" LABEL="D080GB" 

/dev/sdc1: LABEL="D500GB" UUID="dde6aa0b-a8aa-4c73-ba42-f0b6cb45b934" SEC_TYPE="ext2" TYPE="ext3" 


stan@stan-desktop:/$ cat /etc/fstab

# /etc/fstab: static file system information.

#

# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc            /proc           proc    defaults        0       0

# /dev/sda1

UUID=910440c5-7bd2-48e5-a885-85cf80f50c8b /               ext3    relatime,errors=remount-ro 0       1

# /dev/sdb1

UUID=e35501d9-476a-42ac-aa90-e6cf855dda5f /media/diskb    ext3    relatime,errors=remount-ro 0       1

# /dev/sdc1

UUID=dde6aa0b-a8aa-4c73-ba42-f0b6cb45b934 /media/diskc     ext3    relatime,errors=remount-ro 0       1

# /dev/sda5

UUID=8a462438-77e4-4138-86f1-3810c73931f2 none            swap    sw              0       0

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0


stan@stan-desktop:/$ df -h

Filesystem            Size  Used Avail Use% Mounted on

/dev/sda1             272G  6.2G  252G   3% /

varrun               1014M  116K 1013M   1% /var/run

varlock              1014M     0 1014M   0% /var/lock

udev                 1014M   60K 1013M   1% /dev

devshm               1014M   32K 1013M   1% /dev/shm

lrm                  1014M   39M  975M   4% /lib/modules/2.6.24-23-generic/volatile

/dev/sdb1              74G  180M   71G   1% /media/diskb

/dev/sdc1             463G  200M  439G   1% /media/diskc

gvfs-fuse-daemon      272G  6.2G  252G   3% /home/stan/.gvfs

---

### Post by taurus on 2009-04-11
Since both /dev/sdb1 & /dev/sdc1 are ext3, you can just change the ownership of those two mount points from root to your login name, stan, so you can write to them anytime you want.

```
sudo chown -R stan:stan /media/diskb
sudo chown -R stan:stan /media/diskc
ls -la /media
```

---

### Post by stans on 2009-04-11
Excellent ! It works... 

I was almost there, but didn't have the GROUP changed.

Thank You very much.

---

