---
title: "Hard drive disappeared"
date: 2009-04-28
forum: Hardware
---

### Post by gewitty on 2009-04-28
**SOLVED: ** Managed to access the drive through Gparted. The formatting had apparently become corrupted (by the power cut?). Reformatted the whole drive. Problem solved.

 

Can anyone suggest why one of my hard drives is no longer appearing?

It was showing up OK as sdb and appeared as a mounted drive whenever I booted the system. However, after I had a few problems with graphics, I decided to do a complete re-install of 9.04. During my first attempt at this, there was a power failure. After the power came back on, I started the installation again, which went OK, apart from the fact that sdb is no longer showing up. Below is the output of fdisk, blkid, cat /etc/fstab and df -h checks:

dave@dave-desktop:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18662   149902483+  83  Linux
/dev/sda2           18663       19457     6385837+   5  Extended
/dev/sda5           18663       19457     6385806   82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe8a226df

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1      121601   976760001   8e  Linux LVM

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0000513f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       38913   312568641   83  Linux
dave@dave-desktop:~$ 


dave@dave-desktop:~$ sudo blkid
/dev/sda1: UUID="071991b8-1116-4407-8128-179850d03487" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="9b2e9757-ef61-430b-9596-b01949b33093" 
/dev/sdb1: UUID="LEIV1Y-ztlp-k5Qb-dJp2-ZKHx-UijX-IVjuyB" TYPE="lvm2pv" 
/dev/sdc1: UUID="9be6d0b0-d3eb-40d9-a719-50f3a427fd27" SEC_TYPE="ext2" TYPE="ext3" 
dave@dave-desktop:~$ 


dave@dave-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=071991b8-1116-4407-8128-179850d03487 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=9b2e9757-ef61-430b-9596-b01949b33093 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
dave@dave-desktop:~$ 


dave@dave-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             141G  4.4G  130G   4% /
tmpfs                 2.0G     0  2.0G   0% /lib/init/rw
varrun                2.0G  104K  2.0G   1% /var/run
varlock               2.0G     0  2.0G   0% /var/lock
udev                  2.0G  180K  2.0G   1% /dev
tmpfs                 2.0G  440K  2.0G   1% /dev/shm
lrm                   2.0G  2.7M  2.0G   1% /lib/modules/2.6.28-11-generic/volatile
dave@dave-desktop:~$ 



That appears to show some recognition of sdb, but I'm not experienced enough to determine what the fault might be. Any ideas would be welcome.

---

