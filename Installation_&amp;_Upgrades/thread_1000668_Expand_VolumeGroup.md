---
title: "Expand VolumeGroup"
date: 2008-12-03
forum: Installation &amp; Upgrades
---

### Post by TTown on 2008-12-03
This should be easy to the regular server admin but I couldn't get it figured out under linux (took me about an hour under xp64 including research :-/).

My media server at home runs Ubunt Hardy x86_64 (2.6.24-21-generic). /boot (ext3) and /tmp (ext3) are on one hdd (sdb), everything else ( / (xfs)) is on a hardware raid 6 (sda).
I recently added another hdd to my raid setup (areca 3112ml with - now - 7 x 750GB) and expanded and migrated the raid set on hardware level. This worked fine.
Now I would like to make the extra 750GB space available to my volumegroup which does not seem to have noticed that the one hdd it thinks it consists of just grew some extra bytes.


stefan@unterhaltung:~$ sudo vgdisplay                                             --- Volume group ---
  VG Name               VolGroup00
  System ID
  Format                lvm2
  Metadata Areas        1
  Metadata Sequence No  3
  VG Access             read/write
  VG Status             resizable
  MAX LV                0
  Cur LV                2
  Open LV               2
  Max PV                0
  Cur PV                1
  Act PV                1
  VG Size               2.73 TB
  PE Size               64.00 MB
  Total PE              44712
  Alloc PE / Size       44712 / 2.73 TB
  Free  PE / Size       0 / 0
  VG UUID               Jqfec5-tep4-vnLJ-1v5O-uk4O-iRdv-Nx4EE8

stefan@unterhaltung:~$ sudo lvm vgs
  VG         #PV #LV #SN Attr   VSize VFree
  VolGroup00   1   2   0 wz--n- 2.73T    0


Areca's raid manager says:

Raid Set Information
Raid Set Name 	Raid Set # 00
Member Disks 	7
Total Raw Capacity 	5251.1GB
Free Raw Capacity 	0.0GB
Min Member Disk Size 	750.2GB
Raid Set Power State 	Operating
Raid Set State 	Normal


Volume Set Information
Volume Set Name 	ARC-1231-VOL#00
Raid Set Name 	Raid Set # 00
Volume Capacity 	3750.8GB
SCSI Ch/Id/Lun 	0/0/0
Raid Level 	Raid 6
Stripe Size 	64KBytes
Block Size 	512Bytes
Member Disks 	7
Cache Mode 	Write Back
Tagged Queuing 	Enabled
Volume State 	Normal


stefan@unterhaltung:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/mapper/VolGroup00-LogVol00
                     2925985792 2468813344 457172448  85% /
varrun                 1031536       996   1030540   1% /var/run
varlock                1031536         0   1031536   0% /var/lock
udev                   1031536        44   1031492   1% /dev
devshm                 1031536        12   1031524   1% /dev/shm
lrm                    1031536     44968    986568   5% /lib/modules/2.6.24-21-g  eneric/volatile
/dev/sdb1                93504     64032     29472  69% /boot
/dev/sdb2            102348276      5128 102343148   1% /tmp
gvfs-fuse-daemon     2925985792 2468813344 457172448  85% /home/stefan/.gvfs

How do I go about accomplishing this without seriously endangering the data?
I can backup some essential data, but I have no means of backing-up 3TB for a re-install.
Manually tweaking the partition table and deleting and re-establishing partitions without losing data (as I read in one post) seriously scares me.


Thank you

---

### Post by scorp123 on 2008-12-03
Learning Linux LVM, Part 1, by IBM:
[http://www.ibm.com/developerworks/linux/library/l-lvm/](http://www.ibm.com/developerworks/linux/library/l-lvm/)

Learning Linux LVM, Part 2, by IBM:
[http://www.ibm.com/developerworks/library/l-lvm2.html](http://www.ibm.com/developerworks/library/l-lvm2.html)

Your problem is discussed in the second part, chapter "The space problem".

---

