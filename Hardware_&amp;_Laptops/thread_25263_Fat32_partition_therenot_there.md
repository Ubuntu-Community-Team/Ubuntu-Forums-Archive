---
title: "Fat32 partition there/not there"
date: 2005-04-09
forum: Hardware &amp; Laptops
---

### Post by aaroniu on 2005-04-09
I am a new Ubuntu user. I am trying to mount a FAT32 data partition on my second hard drive so I can have read/write access to these files in both Windows and Ubuntu. The partition did not seem to be detected at all by the Ubuntu installation (not sure if this is ordinary behavior or not). When I try to mount it, I get a message that the "special device /dev/hdb1 does not exist". Diagnostic information below:

root@ubuntu:/mnt # cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda6       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdc        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0

/dev/hdb1       /mnt/babel      vfat    rw,auto,uid=1000,gid=1000,umask=0000 0 0
root@ubuntu:/mnt # df -l
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/hda3             38930924   1715572  35237752   5% /
tmpfs                   258248         0    258248   0% /dev/shm
/dev                  38930924   1715572  35237752   5% /.dev
none                      5120      2888      2232  57% /dev
root@ubuntu:/mnt # sudo mount /dev/hdb1
mount: special device /dev/hdb1 does not exist
root@ubuntu:/mnt # sudo mount -a
mount: special device /dev/hdb1 does not exist
root@ubuntu:/mnt # fdisk -l

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        1275    10241406    7  HPFS/NTFS
/dev/hda2            6200        9729    28354725    f  W95 Ext'd (LBA)
/dev/hda3   *        1276        6199    39552030   83  Linux
/dev/hda5            6388        9729    26844583+   7  HPFS/NTFS
/dev/hda6            6200        6387     1510047   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/hdb: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       16709   134215011   42  SFS


In addition to the result from fdisk -l, gparted can see /dev/hdb1 as a fat32 partition, and correctly identifies the filesize (131,069 MB).

Any thoughts?

---

### Post by occy8 on 2005-04-09
Hi should be no prob
first I made the folders 
/mnt/cdrive 
/mnt/ddrive
/mnt/edrive

my fstab looks like this no problems rw access to all partitions
/dev/hda1       /mnt/cdrive    vfat    umask=000       0       0
/dev/hda5       /mnt/ddrive    vfat    umask=000       0       0
/dev/hda6       /mnt/edrive    vfat    umask=000       0       0

good look

---

### Post by aaroniu on 2005-04-09
A few quick clarifying points:

- It is only hdb1 that I am trying to mount. The two CD drives are successfully mounted and I am not worried about trying to mount the NTFS windows partitions.
- The directory I am trying to mount to (/mnt/babel) has already been created.

---

### Post by alastair on 2005-04-09
When you do an "fdisk -l /dev/hdb", you get :

```
Disk /dev/hdb: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/hdb1 1 16709 134215011 42 SFS
```

The odd thing there is the partition type "SFS". Are you sure it is a VFAT partition? Can you double-check with Windows?

I would check the boot messages (for mention of hdb (and context)), and make sure nothing is odd there.

If you cannot get anywhere, I would wonder whether changing the partition type of /dev/hdb1 to something more normal for VFAT might help? Note - I make no guaratees you would not destroy your data though! Be careful.

---

### Post by aaroniu on 2005-04-09
Thanks for the ideas. Booting back into Windows I found it was also unable to see the partition. I ended up adding another small partition in some of the free space on hdb, after which I was able to successfully mount hdb1 in Ubuntu and access my data. Must have lost info on how the drive was supposed to be partitioned at some point during the install, which adding a new partition then fixed. Hey, whatever works!

---

### Post by occy8 on 2005-04-09
There is an interesting thread here. seems to be not uncommon
[http://www.broadbandreports.com/forum/remark,12990536~start=2~mode=flat](http://www.broadbandreports.com/forum/remark,12990536~start=2~mode=flat)

---

