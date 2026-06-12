---
title: "[SOLVED] how to auto-mount sata drive"
date: 2008-07-13
forum: Hardware
---

### Post by shankariyer on 2008-07-13
Hi,

I formatted my new SATA drive(750gb), in addition to two PATA's(320g, 120g) using Partition Magic in Windoze.

> 750gb = 150gb x 2 NTFS partitions + 150gb x 2 EXT3 partitions + Remaining UnallocatedWindoze/Ubuntu do recogonize the drive(s), but gParted reports an error for the NTFS partitions, while it does recogonize other NTFS partitions in PATA's.

What do I do to mount the new drive and partitions available for me to read/write from Hardy ?
> 
# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb10             19G  8.5G  9.4G  48% /
varrun                2.0G  152K  2.0G   1% /var/run
varlock               2.0G     0  2.0G   0% /var/lock
udev                  2.0G  120K  2.0G   1% /dev
devshm                2.0G   36K  2.0G   1% /dev/shm
lrm                   2.0G   44M  1.9G   3% /lib/modules/2.6.24-19-generic/volatile
/dev/sdb11             19G   11G  7.0G  61% /app
/dev/sdb12             19G  173M   18G   1% /db
/dev/sdb1              41G   22G   19G  54% /media/hda1
/dev/sdb5              41G  4.7G   36G  12% /media/hda5
/dev/sdb6              41G   19G   22G  47% /media/hda6
/dev/sdb7              41G  3.3G   37G   9% /media/hda7
/dev/sdb8              21G   20G  520M  98% /media/hda8
/dev/sdb9              21G   17G  3.2G  85% /media/hda9
/dev/sdc5             112G   72G   40G  65% /media/hdb5
/dev/sdb14             21G   14G  6.1G  70% /utl
/dev/sdb13             19G   11G  7.1G  61% /web
> 
# fdisk -l

Disk /dev/sda: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7fef2bee

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               2       78329   629169660    f  W95 Ext'd (LBA)
/dev/sda5               2       19583   157292383+   7  HPFS/NTFS
/dev/sda6           19584       39165   157292383+   7  HPFS/NTFS
/dev/sda7           39166       58747   157292383+  83  Linux
/dev/sda8           58748       78329   157292383+  83  Linux

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x208c208b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        5222    41945683+   7  HPFS/NTFS
/dev/sdb2            5223       38913   270622957+   f  W95 Ext'd (LBA)
/dev/sdb5            5223       10444    41945683+   7  HPFS/NTFS
/dev/sdb6           10445       15666    41945683+   7  HPFS/NTFS
/dev/sdb7           15667       20888    41945683+   7  HPFS/NTFS
/dev/sdb8           20889       23499    20972826    7  HPFS/NTFS
/dev/sdb9           23500       26110    20972826    7  HPFS/NTFS
/dev/sdb10          26111       28600    20000893+  83  Linux
/dev/sdb11          28601       31090    20000893+  83  Linux
/dev/sdb12          31091       33580    20000893+  83  Linux
/dev/sdb13          33581       36070    20000893+  83  Linux
/dev/sdb14          36071       38822    22105408+  83  Linux
/dev/sdb15          38823       38913      730926   82  Linux swap / Solaris

Disk /dev/sdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x68a06a33

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           2       14593   117210240    f  W95 Ext'd (LBA)
/dev/sdc5               2       14593   117210208+   7  HPFS/NTFS

> 
# cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda10
UUID=4d7c15b3-9bec-4a2b-8c1f-96af6cb39d9f /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda11
UUID=2b7edb84-b4ac-45c3-8056-0d02a240f08e /app            ext3    defaults        0       2
# /dev/hda14
UUID=b074a6c5-28ae-4e80-bce6-72d1f8380d40 /db             ext3    defaults        0       2
# /dev/hda1
UUID=9A3475C73475A6C3 /media/hda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/hda5
UUID=13318E7CFBEA72F1 /media/hda5     ntfs    defaults,umask=007,gid=46 0       1
# /dev/hda6
UUID=4CC639F851362644 /media/hda6     ntfs    defaults,umask=007,gid=46 0       1
# /dev/hda7
UUID=ACBE026EB6B9D619 /media/hda7     ntfs    defaults,umask=007,gid=46 0       1
# /dev/hda8
UUID=0252BA9ACB0A0390 /media/hda8     ntfs    defaults,umask=007,gid=46 0       1
# /dev/hda9
UUID=22DF31C4BEECDCC1 /media/hda9     ntfs    defaults,umask=007,gid=46 0       1
# /dev/hdb5
UUID=3AF49919F498D909 /media/hdb5     ntfs    defaults,umask=007,gid=46 0       1
# /dev/hda13
UUID=6acf28d7-9ed8-45fd-a638-22f3ab15fbbc /utl            ext3    defaults        0       2
# /dev/hda12
UUID=003c10bc-4e2f-4a76-bcb1-a07f6dafffc1 /web            ext3    defaults        0       2
# /dev/hda15
UUID=9b2be826-f73d-400f-9518-50697f4d0cc6 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
Thanks.

---

### Post by shankariyer on 2008-07-13
I fixed this as this -

1. Backup your current /etc/fstab
2. Do a **sudo fdisk -l** to get the volume names ( e.g. /dev/sda7 )
3. With the volume-name, find the UUID ( e.g. **sudo vol_id -u /dev/sda7** )
4. Create new entries in /etc/fstab as sudo, for the newly added partitions/disks ( see my current /etc/fstab )
5. To mount 'ext3' partitions, format them using 'gparted' and follow steps 2,3 and 4

> 
# **cat /etc/fstab**
# /etc/fstab: static file system information.
#
# <file system>                           <mount point>  <type>  <options>            <dump>  <pass>
proc                                      /proc          proc defaults                   0 0
UUID=4d7c15b3-9bec-4a2b-8c1f-96af6cb39d9f /              ext3 defaults,errors=remount-ro 0 1 # /dev/hda10
UUID=2b7edb84-b4ac-45c3-8056-0d02a240f08e /app           ext3 defaults                   0 2 # /dev/hda11
UUID=b074a6c5-28ae-4e80-bce6-72d1f8380d40 /db            ext3 defaults                   0 2 # /dev/hda14
UUID=9A3475C73475A6C3                     /media/hda1    ntfs defaults,umask=007,gid=46  0 1 # /dev/hda1
UUID=13318E7CFBEA72F1                     /media/hda5    ntfs defaults,umask=007,gid=46  0 1 # /dev/hda5
UUID=4CC639F851362644                     /media/hda6    ntfs defaults,umask=007,gid=46  0 1 # /dev/hda6
UUID=ACBE026EB6B9D619                     /media/hda7    ntfs defaults,umask=007,gid=46  0 1 # /dev/hda7
UUID=0252BA9ACB0A0390                     /media/hda8    ntfs defaults,umask=007,gid=46  0 1 # /dev/hda8
UUID=22DF31C4BEECDCC1                     /media/hda9    ntfs defaults,umask=007,gid=46  0 1 # /dev/hda9
UUID=3AF49919F498D909                     /media/hdb5    ntfs defaults,umask=007,gid=46  0 1 # /dev/hdb5
UUID=6acf28d7-9ed8-45fd-a638-22f3ab15fbbc /utl           ext3 defaults                   0 2 # /dev/hda13
UUID=003c10bc-4e2f-4a76-bcb1-a07f6dafffc1 /web           ext3 defaults                   0 2 # /dev/hda12
UUID=9b2be826-f73d-400f-9518-50697f4d0cc6 none           swap sw                         0 0 # /dev/hda15
/dev/scd0                                 /media/cdrom0  udf,iso9660 user,noauto,exec    0 0
/dev/fd0                                  /media/floppy0 auto rw,user,noauto,exec        0 0

# -----> New SATA Drive Partitions <-----
UUID=6CB06795B0676494                     /media/hda10   ntfs defaults,umask=007,gid=46  0 1 # NTFS - l-drive
UUID=82788C37788C2BCB                     /media/hda11   ntfs defaults,umask=007,gid=46  0 1 # NTFS - m-drive

UUID=2b2295ab-a996-47bd-9269-e7fcd9814d73 /sata_media    ext3 defaults                   0 2 # /dev/sda7
UUID=1e5952c6-3720-45c7-8b85-599c670beec4 /sata_utl      ext3 defaults                   0 2 # /dev/sda8


---

