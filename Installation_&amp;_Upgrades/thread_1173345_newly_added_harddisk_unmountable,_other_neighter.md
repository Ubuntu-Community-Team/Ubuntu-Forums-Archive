---
title: "newly added harddisk unmountable, other neighter"
date: 2009-05-29
forum: Installation &amp; Upgrades
---

### Post by RobertLos on 2009-05-29
Yesterday I bought an extra hard disk for back-up purposes. After solving some problems with grub (the sequence of /dev/sd? devices changed) I was able to partition the new disk with a small ntfs primary partition and an 512 GB ext3 partition in the extended partition.

fdisk -l shows following:

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfd7011cd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       17947   144159246    7  HPFS/NTFS
/dev/sda2           17948       24321    51199155    f  W95 Ext'd (LBA)
/dev/sda5           17948       24321    51199123+   7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0008789c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       60424   485355748+  83  Linux
/dev/sdb2           60425       60801     3028252+   f  W95 Ext'd (LBA)
/dev/sdb5           60425       60801     3028221   82  Linux swap / Solaris

Disk /dev/sdc: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0006c1cd

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       10199    81923436    7  HPFS/NTFS
/dev/sdc2           10200       77825   543205845    f  W95 Ext'd (LBA)
/dev/sdc5           10200       77825   543205813+  83  Linux

Disk /dev/sdd: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0d480d48

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1        5979    48026286    7  HPFS/NTFS
/dev/sdd2            5980       14946    72027427+   f  W95 Ext'd (LBA)
/dev/sdd5            5980       14946    72027396    7  HPFS/NTFS

Disk /dev/sde: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd4c9099d

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1       47201   379142001    7  HPFS/NTFS

Looks like a lot of disks. The new disk is /dev/sdc.

I added a mountpoint /var2 and added the following line in /etc/fstab

/dev/sdc1       /media/winxp_e     ntfs-3g  rw,users,gid=users,umask=0002,nls=utf8 0 0
/dev/sdc5 /var2		  ext3	  defaults,errors=remount-ro 0 1
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

sudo mount /dev/sdc5 tells 
mount: /dev/sdc5 already mounted or /var2 busy
umount /dev/sdc5 says umount: /dev/sdc5 is not mounted (according to mtab)

gparted suddenly shows a lot of /dev/mapper devices.

When booting in windows-XP I can see the new drive and use the ntfs partition.

all disks can not be mounted except the boot disk (/dev/sdb1)

any ideas?

I upgrade from 5.04 to 9.04 with all in between steps.

thanks

---

### Post by Mark Phelps on 2009-05-30
Know it may sound silly, but would change the /var2 mount to a /media mount.

Also, would remove the sdc5 line from fstab and manually mount sdc5 without the errors option.  It may be remounting the partition over and over, encountering errors each time, and remounting it again.  At least this way, if there are errors, you will see the messages in the terminal.

---

### Post by RobertLos on 2009-06-04
Dear Mark,

Thanks for answering. I kind of sorted things out. It does not matter where the mount point is. /media is used for either windows formated ntfs or FAT formatted drives or for removable media. You can of course use this for a new hard disk. Since I use backup-manager and the new disk is internally installed I figured that /var2 would be a good position since I add a directory /vars/archives there so new backups would land (after changing backup-manager.conf) on a different disk.

The problem was caused by the software raid functionality. It looks like the new disk was treated as a raid device and therefore unmountable for other linux processes, including mounting by hand. Removing mdadm and libdmraid solved the problem.

Did cost me some time to figure out however. The boot process is now greatly sped up.

Thanks

Robert

---

