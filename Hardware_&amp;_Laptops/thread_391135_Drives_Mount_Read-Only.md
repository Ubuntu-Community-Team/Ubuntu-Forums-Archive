---
title: "Drives Mount Read-Only"
date: 2007-03-22
forum: Hardware &amp; Laptops
---

### Post by Netzilla on 2007-03-22
I recently re-formatted two of my drives, one internal and one external from FAT32 to ext2 and ext3.  However, now both of these drives will only mount read-only.  If anyone can help me, I would be very greatful.  The drives in question are /dev/hdd1 (internal, ext3) and /dev/sda6 (external, ext2)

******* Contents of /etc/fstab ********
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hda5       /media/hda5     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/hdb1       /media/hdb1     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/hdd1       /media/hdd1     ext3    rw,suid,dev,exec,auto,nouser,async	0       1
/dev/hdb2       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
**************************************

******* Results of fdisk -l ********
Disk /dev/hda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1216     9767488+   7  HPFS/NTFS
/dev/hda2            1217        4998    30378915    f  W95 Ext'd (LBA)
/dev/hda5            1217        4998    30378883+   b  W95 FAT32

Disk /dev/hdb: 6480 MB, 6480101376 bytes
255 heads, 63 sectors/track, 787 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1         255     2048256    b  W95 FAT32
/dev/hdb2             724         787      514080   82  Linux swap / Solaris
/dev/hdb3             256         723     3759210   83  Linux

Partition table entries are not in disk order

Disk /dev/hdd: 20.4 GB, 20491075584 bytes
255 heads, 63 sectors/track, 2491 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1               1        2491    20008926   83  Linux

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               2        4862    39045982+   f  W95 Ext'd (LBA)
/dev/sda5               2        2551    20482843+   b  W95 FAT32
/dev/sda6            2552        4862    18563076   83  Linux
**************************************

---

### Post by taurus on 2007-03-22
How do you mount those two drives, /dev/hdd1 & /dev/sda6?  You can edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and add these two lines to the end of it.

```
/dev/hdd1   /media/hdd1   ext3   defaults   0   1
/dev/sda6   /media/sda6   ext2   defaults   0   1
```
Save the changes.  Then, create two mount points and mount them.

```
sudo mkdir /media/hdd1 /media/sda6
sudo mount -a
df -h
```
Now, if you want to be able to write to them, then just change the ownership of those two mount points from root to your login name, assuming it's **netzilla**.

```
sudo chown -R **netzilla**:**netzilla** /media/hdd1
sudo chown -R **netzilla**:**netzilla** /media/sda6
ls -la /media
```

---

### Post by Netzilla on 2007-03-22
> **taurus said:**
> How do you mount those two drives, /dev/hdd1 & /dev/sda6?  

In the case of hdd1, it's just mounted on bootup from the fstab parameters.  For the sda6 (my external drive), it's auto-detected by Ubuntu.  Prior to the re-format, both of these drives mounted as Read/Write.

> 
You can edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and add these two lines to the end of it.

```
/dev/hdd1   /media/hdd1   ext3   defaults   0   1
/dev/sda6   /media/sda6   ext2   defaults   0   1
```
Save the changes.  Then, create two mount points and mount them.

```
sudo mkdir /media/hdd1 /media/sda6
sudo mount -a
df -h
```


I've tried various edits of the fstab file, including using the "defaults" setting and while the drives mount, they were still read-only.

> 
Now, if you want to be able to write to them, then just change the ownership of those two mount points from root to your login name, assuming it's **netzilla**.

```
sudo chown -R **netzilla**:**netzilla** /media/hdd1
sudo chown -R **netzilla**:**netzilla** /media/sda6
ls -la /media
```

Hmmm.  Looking at the drive's properties, it does say that "root" is the owner, so this is probably my problem.  Will I have to do this manually every time I boot into Ubuntu or is there a way I can configure it to do this automatically?

Thanks for the help.

---

