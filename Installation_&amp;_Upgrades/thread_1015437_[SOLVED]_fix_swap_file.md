---
title: "[SOLVED] fix swap file"
date: 2008-12-18
forum: Installation &amp; Upgrades
---

### Post by upchucky on 2008-12-18
My system is completely functional, but i noticed this error on bootup,


VFS: Can't find ext3 filesystem on dev sda4.


The problem is that dev sda4 is my 1 gig swap file, so it should not be a ext3 filesystem.

my ubuntu install is ext3 on dev sda6

what file do i need to edit to get rid of the reference to the ext3 on dev sda4?

---

### Post by taurus on 2008-12-18
Look in /etc/fstab if you want to remove the entry for /dev/sda4.  

Can you post the outputs of these commands from a terminal?

```
sudo fdisk -l
sudo blkid
cat /etc/fstab
free -m
```

---

### Post by upchucky on 2008-12-18
Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xeb275b50

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           6       48163+   6  FAT16
/dev/sda2   *           7        1744    13960485    7  HPFS/NTFS
/dev/sda3            1876       12161    82622295    f  W95 Ext'd (LBA)
/dev/sda4            1745        1875     1052257+  82  Linux swap / Solaris
/dev/sda5            1876        7017    41303083+   7  HPFS/NTFS
/dev/sda6            7018       12161    41319148+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0004ce2e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        5291    42499926   83  Linux
/dev/sdb2            5292       12161    55183275    7  HPFS/NTFS
electric@XPS-Laptop:~$ 

electric@XPS-Laptop:~$ sudo blkid
sudo: unable to resolve host XPS-Laptop
/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D5-041B" TYPE="vfat" 
/dev/sda2: TYPE="ntfs" UUID="6C74A95574A922B6" 
/dev/sda5: TYPE="ntfs" UUID="1174E0F45EF02D59" LABEL="Files" 
/dev/sda6: UUID="bd934b7a-0fd5-4863-bbf3-554d010199a4" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb1: UUID="2d9a271b-7489-4d99-8576-0b6c6e05ac30" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda4: TYPE="swap" 
/dev/sdb2: UUID="0E84E4E27500FBDD" TYPE="ntfs" 
electric@XPS-Laptop:~$ 

electric@XPS-Laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda7
UUID=bd934b7a-0fd5-4863-bbf3-554d010199a4 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=07D5-041B  /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda2
UUID=6C74A95574A922B6 /media/sda2     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=1174E0F45EF02D59 /media/sda5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda6
UUID=89ef2fb0-0e3f-46eb-b6af-faffd3dcaf63 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
# /media/sda4 (25gig disk)
# /dev/sda4
#UUID=58fced66-e616-48cc-8d0f-13ccdcb58255 /media/sda4 ext3 umask=007 0 0


electric@XPS-Laptop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          2027        469       1557          0         16        230
-/+ buffers/cache:        223       1804
Swap:            0          0          0
electric@XPS-Laptop:~$ 


Thanks for the quick reply, 
Looks like the swap is not being used?

---

### Post by taurus on 2008-12-18
> **upchucky said:**
> Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xeb275b50

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           6       48163+   6  FAT16
/dev/sda2   *           7        1744    13960485    7  HPFS/NTFS
/dev/sda3            1876       12161    82622295    f  W95 Ext'd (LBA)
/dev/sda4            1745        1875     1052257+  82  Linux swap / Solaris
/dev/sda5            1876        7017    41303083+   7  HPFS/NTFS
**[COLOR="Blue"]/dev/sda6            7018       12161    41319148+  83  Linux[/COLOR]**

Partition table entries are not in disk order

Disk /dev/sdb: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0004ce2e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        5291    42499926   83  Linux
/dev/sdb2            5292       12161    55183275    7  HPFS/NTFS
electric@XPS-Laptop:~$ 

electric@XPS-Laptop:~$ sudo blkid
sudo: unable to resolve host XPS-Laptop
/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D5-041B" TYPE="vfat" 
/dev/sda2: TYPE="ntfs" UUID="6C74A95574A922B6" 
/dev/sda5: TYPE="ntfs" UUID="1174E0F45EF02D59" LABEL="Files" 
**[COLOR="Blue"]/dev/sda6: UUID="bd934b7a-0fd5-4863-bbf3-554d010199a4" SEC_TYPE="ext2" TYPE="ext3" [/COLOR]**
/dev/sdb1: UUID="2d9a271b-7489-4d99-8576-0b6c6e05ac30" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda4: TYPE="swap" 
/dev/sdb2: UUID="0E84E4E27500FBDD" TYPE="ntfs" 
electric@XPS-Laptop:~$ 

electric@XPS-Laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda7
UUID=bd934b7a-0fd5-4863-bbf3-554d010199a4 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=07D5-041B  /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda2
UUID=6C74A95574A922B6 /media/sda2     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=1174E0F45EF02D59 /media/sda5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda6
**[COLOR="Blue"]UUID=89ef2fb0-0e3f-46eb-b6af-faffd3dcaf63 none            swap    sw              0       0[/COLOR]**
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
# /media/sda4 (25gig disk)
# /dev/sda4
#UUID=58fced66-e616-48cc-8d0f-13ccdcb58255 /media/sda4 ext3 umask=007 0 0


electric@XPS-Laptop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          2027        469       1557          0         16        230
-/+ buffers/cache:        223       1804
Swap:            0          0          0
electric@XPS-Laptop:~$ 


Thanks for the quick reply, 
Looks like the swap is not being used?

You are using the wrong UUID in /etc/fstab for your swap.

Therefore, you need to edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and replace this line

```

UUID=89ef2fb0-0e3f-46eb-b6af-faffd3dcaf63 none            swap    sw              0       0

```
with this one.

```
/dev/sda4   none   swap   sw   0   0
```
Save the change and close down gedit editing window.  Then run

```
sudo mount -a
free -m
```

---

### Post by upchucky on 2008-12-18
Ok thanks, the following is the results.

electric@XPS-Laptop:~$ sudo mount -a
sudo: unable to resolve host XPS-Laptop
mount: wrong fs type, bad option, bad superblock on /dev/sda4,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

electric@XPS-Laptop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          2027        471       1555          0         16        230
-/+ buffers/cache:        223       1803
Swap:            0          0          0
electric@XPS-Laptop:~$ 


and this is the edited fstab.

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda7
UUID=bd934b7a-0fd5-4863-bbf3-554d010199a4 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=07D5-041B  /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda2
UUID=6C74A95574A922B6 /media/sda2     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=1174E0F45EF02D59 /media/sda5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda6
#UUID=89ef2fb0-0e3f-46eb-b6af-faffd3dcaf63 none            swap    sw              0       0
/dev/sda4   none   swap   sw   0   0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
# /media/sda4 (25gig disk)
# /dev/sda4
#UUID=58fced66-e616-48cc-8d0f-13ccdcb58255 /media/sda4 ext3 umask=007 0 0
/dev/sda4 /storage ext3 defaults 0 0


shouldn't the last line be removed also?

---

### Post by upchucky on 2008-12-18
removed last line and all is well, many thanks.

---

### Post by taurus on 2008-12-18
> **upchucky said:**
> Ok thanks, the following is the results.

electric@XPS-Laptop:~$ sudo mount -a
sudo: unable to resolve host XPS-Laptop
mount: wrong fs type, bad option, bad superblock on /dev/sda4,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

electric@XPS-Laptop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          2027        471       1555          0         16        230
-/+ buffers/cache:        223       1803
Swap:            0          0          0
electric@XPS-Laptop:~$ 


and this is the edited fstab.

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda7
UUID=bd934b7a-0fd5-4863-bbf3-554d010199a4 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=07D5-041B  /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda2
UUID=6C74A95574A922B6 /media/sda2     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=1174E0F45EF02D59 /media/sda5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda6
#UUID=89ef2fb0-0e3f-46eb-b6af-faffd3dcaf63 none            swap    sw              0       0
/dev/sda4   none   swap   sw   0   0[/B]
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
# /media/sda4 (25gig disk)
# /dev/sda4
#UUID=58fced66-e616-48cc-8d0f-13ccdcb58255 /media/sda4 ext3 umask=007 0 0
**[COLOR="Blue"]/dev/sda4 /storage ext3 defaults 0 0[/COLOR]**

shouldn't the last line be removed also?

Yeah, not sure why the last line is even there since /dev/sda4 is swap, not an ext3 filesystem.  So, remove it.

Now run
```
sudo mkswap /dev/sda4
sudo mount -a
free -m
```

---

### Post by upchucky on 2008-12-19
Hmm,

seems that the swap is now functional, am I right to assume that the unresolved host error is because I am on the active partition and the error would not happen if i did the commands from a live cd?

electric@XPS-Laptop:~$ sudo mkswap /dev/sda4
sudo: unable to resolve host XPS-Laptop
[sudo] password for electric: 
/dev/sda4: Device or resource busy
electric@XPS-Laptop:~$ sudo mount -a
sudo: unable to resolve host XPS-Laptop
electric@XPS-Laptop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          2027       1182        844          0        193        634
-/+ buffers/cache:        353       1673
Swap:         1027          0       1027
electric@XPS-Laptop:~$

---

### Post by upchucky on 2008-12-19
found another thread that resolved the hostname error.

---

