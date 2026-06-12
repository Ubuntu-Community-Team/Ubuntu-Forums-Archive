---
title: "Cannot mount volume"
date: 2008-09-08
forum: General Help
---

### Post by bkbilly on 2008-09-08
I have an mp3 player but I can't mount it.
It was working till i went to properties of my mp3 and then to Volume. In the "mount options" I wrote something inside. when i remounted my mp3 it couldn't mount and it was saying that message: _"Invalid mount option when attempting to mount the volume 'IRIVER'."_
I tried to put this on terminal: _sudo mount /dev/sdd1 /media/iriver_  but nothing...
My iriver is fat32

here is my "/etc/fstab"
```

# Removable media	mount point		fs-type		options				dump-freq pass-num
/dev/scd0		/media/cdrom0		udf,iso9660	user,noauto,exec,utf8			0 0
/dev/sdd1		/media/iriver		vfat		iocharset=utf8,umask=000		0 0

# device name		mount point		fs-type		options				dump-freq pass-num
/dev/sda1		/media/windows		ntfs-3g		defaults,locale=en_US.UTF-8		0 0
/dev/sda2		/media/music		ntfs-3g		defaults,locale=en_US.UTF-8		0 0
/dev/sda3		/media/billy		ntfs-3g		defaults,locale=en_US.UTF-8		0 0
/dev/sdb2		/media/videos		ntfs-3g		defaults,locale=en_US.UTF-8		0 0

```

here is my "sudo fdisk l"
```

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xaf8d71d6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14359   115337216    7  HPFS/NTFS
/dev/sda2           14360       32634   146793937    7  HPFS/NTFS
/dev/sda3           32635       60801   226251424+   7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000a9616

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1          93      746991   82  Linux swap / Solaris
/dev/sdb2            6541       30401   191663480+   7  HPFS/NTFS
/dev/sdb3   *          94        6540    51785527+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdc: 20.0 GB, 20000268288 bytes
255 heads, 63 sectors/track, 2431 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1549c458

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        2431    19526976    c  W95 FAT32 (LBA)

Disk /dev/sdd: 1031 MB, 1031798272 bytes
255 heads, 63 sectors/track, 125 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x91f72d24

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1         126     1007584    b  W95 FAT32
Partition 1 has different physical/logical endings:
     phys=(124, 254, 63) logical=(125, 112, 50)

```

and here is my "/etc/mtab"
```
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.24-19-generic/volatile tmpfs rw 0 0
/dev/sda1 /media/windows fuseblk rw,nosuid,nodev,noatime,allow_other,blksize=4096 0 0
/dev/sda2 /media/music fuseblk rw,nosuid,nodev,noatime,allow_other,blksize=4096 0 0
/dev/sda3 /media/billy fuseblk rw,nosuid,nodev,noatime,allow_other,blksize=4096 0 0
/dev/sdb2 /media/videos fuseblk rw,nosuid,nodev,noatime,allow_other,blksize=4096 0 0
securityfs /sys/kernel/security securityfs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/bkbilly/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=bkbilly 0 0
/dev/sdd1 /media/iriver vfat rw 0 0
```

I searched in the forum for a solution but I couldn't find anything to work!
**[COLOR="DarkGreen"]Please help me!!![/COLOR]**

---

