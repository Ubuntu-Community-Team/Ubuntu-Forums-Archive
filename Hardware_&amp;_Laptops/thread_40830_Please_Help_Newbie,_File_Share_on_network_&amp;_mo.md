---
title: "Please Help Newbie, File Share on network &amp; mount"
date: 2005-06-10
forum: Hardware &amp; Laptops
---

### Post by registerera on 2005-06-10
I would like to share the harddrives on ubuntu pc with windows pc. Both ubuntu/windows computers are connected directly with a nic, and have their own nics for internet via a router.

I installed ubuntu in a raid, and then created a raid partition for the swap. At least that is what I think i have done, I have a list of drives from fdisk below, i may be wrong.

I have tried setting up samba and mounting drives on boot, but it does not work, and i dont know what is wrong. I think the way i have network and internet seperately is causing the problem, because I keep setting the Location for the NICs (eth0 and eth1) in System | Admin | Networking to HOMENET and when I go to check that it is set after reboot or logout, the location becomes blank again. Is there an expert in the house? I put fstab below fdisk as well, I know this is lots of reading but can anyone help me?


# fdisk -l

Disk /dev/sda: 18.3 GB, 18351959040 bytes
255 heads, 63 sectors/track, 2231 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         263     2112516    7  HPFS/NTFS
/dev/sda2             264         709     3582495    7  HPFS/NTFS
/dev/sda3            1521        2231     5711107+   f  W95 Ext'd (LBA)
/dev/sda4             711        1519     6498292+  83  Linux
/dev/sda5            1521        1610      722893+  82  Linux swap / Solaris
/dev/sda6   *        1611        2231     4988151   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 18.3 GB, 18351959040 bytes
255 heads, 63 sectors/track, 2231 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         263     2112516    7  HPFS/NTFS
/dev/sdb2             264         352      714892+   7  HPFS/NTFS
/dev/sdb3             353        1520     9381960    7  HPFS/NTFS
/dev/sdb4            1521        2231     5711107+   f  W95 Ext'd (LBA)
/dev/sdb5            1521        1610      722893+  82  Linux swap / Solaris
/dev/sdb6   *        1611        2231     4988151   83  Linux

Disk /dev/hde: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hde1   *           1         449     3606561    7  HPFS/NTFS
/dev/hde2             450        4865    35471520    f  W95 Ext'd (LBA)
/dev/hde5             450        4865    35471488+   7  HPFS/NTFS


Has been awhile since I stopped using ubuntu...because I spent so much time without success setting up networking for windows users to access files. Right now I can access windows shares on the other computer through Applications | Run App: smb://192.168.0.2/drive (H)   and write to it as well, but windows cant do same when I'm in ubuntu.


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sdb6       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda6       /home           ext3    defaults        0       2
/dev/sda5       none            swap    sw              0       0
/dev/sdb5       none            swap    sw              0       0
/dev/sdb2       /home/jim/drive_J      ntfs ro,umask=0222,uid=1000,gid=1000 0 0
/dev/hde5       /home/jim/drive_G    ntfs ro,umask=0222,uid=1000,gid=1000 0 0
/dev/hde1       /home/jim/drive_C    ntfs ro,umask=0222,uid=1000,gid=1000 0 0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

# //192.168.0.2/drive%20(H) /home/jim/drive_H smbfs credentials=/root/.smbcredentials,dmask=777,fmask=777 0  0
# //192.168.0.2/drive%20(E) /home/jim/drive_E smbfs credentials=/root/.smbcredentials,dmask=777,fmask=777 0  0

---

