---
title: "NTFS partition"
date: 2007-04-27
forum: Hardware &amp; Laptops
---

### Post by staf4t5 on 2007-04-27
Everytime i click on my ntfs partition i get this error message: hal-storage-fixed-mount-all-options refused uid 1000

I have tried ntfs-3g pack but it also gives me problems

---

### Post by lw5 on 2007-04-27
You should post your /etc/fstab here so we can see what might be the problem..

---

### Post by staf4t5 on 2007-04-27
My ntfs partitions are on my sata drive i think its sdb1...

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=eba3be21-e2c5-4717-a97d-ddc00bfc0d7f /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb5
UUID=d8872e84-feb9-42d3-ba57-9e1346022666 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by lw5 on 2007-04-27
I don't think it's in there since sdb1 seems to be an ext (=linux) partition and sdb5 is your swap partition.
So you should probably look at something like [_this_](https://help.ubuntu.com/community/AutomaticallyMountPartitions)

---

### Post by staf4t5 on 2007-04-27
thanks lw5.I was almost gonna give up.It worked now i can access my ntfs partitions.

---

### Post by staf4t5 on 2007-05-25
This is my current fstab but the diskmounter util did not work again after i reinstalled...
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=0eec065a-085e-44d5-9d6d-defb03d1e1da /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=d8872e84-feb9-42d3-ba57-9e1346022666 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
#Added by diskmounter utility
/dev/sdb1 /media/sdb1 vfat rw,user,fmask=0133,dmask=0022,uid=1000,gid=1000 0 0

---

### Post by staf4t5 on 2007-05-25
ok got it working again...Figured out wot was wrong.](*,)

---

### Post by obsrv on 2007-10-23
My fstab is:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb2
UUID=b35b3d2f-a6a2-4484-8414-dd1673cf610a /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=E0043BE8043BBFF8 /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdb1
UUID=C8A08C2FA08C25D2 /media/sdb1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdb3
UUID=0aa448a9-5602-44a9-afbc-768f56985154 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

```

and I can't access sdc1, as I understand it's not defined in fstab, how do I define it? O_o

How about this?:::
```
obsrv@obsrv-desktop:~$ sudo mount /dev/sdc1 /mnt/
$MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/sdc1': Input/output error
NTFS is either inconsistent, or you have hardware faults, or you have a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows TWICE. The usage of the /f parameter is very
important! If you have SoftRAID/FakeRAID then first you must activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for the details.
obsrv@obsrv-desktop:~$

```

---

### Post by sethvath on 2007-10-28
obsrv, install ntfsprogs/ntfs-tools and do the following

ntfsfix /dev/sdaX where X is the number of your partition. in your case it should be sdc1

post a reply here if it works for you. Makes it easy for the next person searching for a similar solution

---

