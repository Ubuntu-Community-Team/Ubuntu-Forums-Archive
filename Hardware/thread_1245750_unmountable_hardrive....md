---
title: "unmountable hardrive..."
date: 2009-08-20
forum: Hardware
---

### Post by BadEyedia on 2009-08-20
I have a 500g external hard drive that I am trying to connect to my laptop. I know that the drive works, because I had just unplugged it from the system and it was working fine. Five minutes later nothing. I ran sudo tail -f /var/log/syslog, and this was the output:

Aug 20 22:01:16 Badeyedia kernel: [  892.054400] sd 4:0:0:0: [sdb] Write Protect is off
Aug 20 22:01:16 Badeyedia kernel: [  892.054411] sd 4:0:0:0: [sdb] Mode Sense: 23 00 00 00
Aug 20 22:01:16 Badeyedia kernel: [  892.054418] sd 4:0:0:0: [sdb] Assuming drive cache: write through
Aug 20 22:01:16 Badeyedia kernel: [  892.055729] sd 4:0:0:0: [sdb] 976773168 512-byte hardware sectors: (500 GB/465 GiB)
Aug 20 22:01:16 Badeyedia kernel: [  892.057542] sd 4:0:0:0: [sdb] Write Protect is off
Aug 20 22:01:16 Badeyedia kernel: [  892.057551] sd 4:0:0:0: [sdb] Mode Sense: 23 00 00 00
Aug 20 22:01:16 Badeyedia kernel: [  892.057558] sd 4:0:0:0: [sdb] Assuming drive cache: write through
Aug 20 22:01:16 Badeyedia kernel: [  892.057569]  sdb:
Aug 20 22:01:16 Badeyedia kernel: [  892.088818] sd 4:0:0:0: [sdb] Attached SCSI disk
Aug 20 22:01:16 Badeyedia kernel: [  892.088994] sd 4:0:0:0: Attached scsi generic sg2 type 0

I tried using the mount command with no luck. Any help would be appreciated appreciated...

---

### Post by vedek on 2009-08-21
try doing this
 
```
 sudo fdisk -l
```
 
and also ```
cat /etc/fstab
```
 
and ```
cat /etc/mtab
```
 
post back what you get and we can take it from there.

---

### Post by BadEyedia on 2009-08-25
Sorry it took so long...

In order:

```
Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           8       64228+  de  Dell Utility
/dev/sda2   *           9        5512    44210880    7  HPFS/NTFS
/dev/sda3            5513        7296    14329980    5  Extended
/dev/sda5            5513        7215    13679316   83  Linux
/dev/sda6            7216        7296      650601   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x21eeb7c9

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x44fdfe06

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       19457   156288321    c  W95 FAT32 (LBA)

```

```
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=e9fdced6-61b4-489f-a2af-a33b7a153496 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=7ed40d7a-b6fe-4656-a231-ca342f6d857e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```
```

/dev/sda5 / ext3 rw,relatime,errors=remount-ro 0 0
tmpfs /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,nosuid,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
tmpfs /dev/shm tmpfs rw,nosuid,nodev 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=620 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0
lrm /lib/modules/2.6.28-13-generic/volatile tmpfs rw,mode=755 0 0
securityfs /sys/kernel/security securityfs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/badeye/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=badeye 0 0
/dev/sdc1 /media/MY\040BOOK vfat rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush 0 0
```

---

### Post by vedek on 2009-08-28
type ```
mount /dev/sdc1
```

---

### Post by BadEyedia on 2009-08-31
First off I just wanted to say thanks for the reply—unfortunately it did not work; but, I do have an idea; as far as I can tell the problem has to do with the partition boot file. The reason I say this is because the information is still intact. I have been able to use recovery software to get some of the files back, but with over 100 gigs of information, this is somewhat unrealistic and painstakingly long. Therefore, I am looking for a way to reformat the drive boot file without damaging the files on the drive . I have heard that this is a possible process but extremely complicated. If any one is able to give any suggestions that would be great.

---

