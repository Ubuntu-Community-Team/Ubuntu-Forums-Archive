---
title: "Hard Drive Missing"
date: 2010-01-25
forum: Hardware
---

### Post by Rodney9 on 2010-01-25
Hello, I used to be able to mount my first hard drive sda, a WD 320GB internal, it has window xp on it, but now I can not mount it.
In Pysdm it shows as a ext 4 Samsung , the same as sdb, strange

Here is what fdisk says and it seems correct -

```

$ sudo fdisk -l
[sudo] password 

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb8e05a14

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38913   312568641    7  HPFS/NTFS

Disk /dev/sdc: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb8e05a15

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       38913   312568641    7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41570539

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       18662   149902483+  83  Linux
/dev/sdb2           18663       19457     6385837+   5  Extended
/dev/sdb5           18663       19457     6385806   82  Linux swap / Solaris

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0003d5b1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1              1      121602   976761560    7  HPFS/NTFS
``` 

My fstab shows - 

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc         defaults                  0  0  
# / was on /dev/sdb1 during installation
UUID=057d14c4-2395-44b2-bec8-b48581dcf056  /               ext4         defaults                  0  1  
# swap was on /dev/sdb5 during installation
UUID=ec671497-3cc4-4d85-a12d-51496fc64467  none            swap         sw                        0  0  
/dev/scd0                                  /media/cdrom0   udf,iso9660  user,noauto,exec,utf8     0  0  
/dev/fd0                                   /media/floppy0  auto         rw,user,noauto,exec,utf8  0  0  
/dev/sdc1                                  /media/sdc1     ntfs         defaults                  0  0  
/dev/sdd1                                  /media/sdd1     ntfs         defaults                  0  0 
```

What is going on ? ,  sda doesn't even show, I tried adding -

```
/dev/sda1                                  /media/sda1     ntfs         defaults                  0  0  
```

but that made no difference.

Please help.

---

### Post by Rodney9 on 2010-01-26
sudo mkdir /media/sda1
sudo mount -t ntfs /dev/sda1 /media/sda1

Fixed Thanks DocDan

---

### Post by pooky2483 on 2011-11-13
> **Rodney9 said:**
> sudo mkdir /media/sda1
sudo mount -t ntfs /dev/sda1 /media/sda1

Fixed Thanks DocDan

I#m having the same trouble, Ive got four HD's, the first one has my OS on and the next 3 are;
sdb1 Win-Storage
sdc1 Win-MyDocs
sdd1 Win-Video

I noticed I was having problems after one of these programs;
Clam Antivirus (Only installed it to try it)
CompizConfig Settings Manager
Storage Device Manager (I ran it to check my Win-Video drive, and others, untill I saw the error)

Afterwards I noticed 'Win-MyDocs' was missing. I can get to it via browse network'
When I got there, I noticed something weird, it was showing the contents of 'Win-Video' in 'Win-MyDocs' and in 'Win-Video' there was nothing.

mount gives;
/dev/sda1 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
/dev/sdb1 on /media/Win-Storage type fuseblk (rw,noexec,nosuid,nodev,allow_other,blksize=4096)
/dev/sdc1 on /media/Win-MyDocs type fuseblk (rw,noexec,nosuid,nodev,allow_other,blksize=4096)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/peter/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=peter)

sudo fdisk -l gives
/dev/sda1 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
/dev/sdb1 on /media/Win-Storage type fuseblk (rw,noexec,nosuid,nodev,allow_other,blksize=4096)
/dev/sdc1 on /media/Win-MyDocs type fuseblk (rw,noexec,nosuid,nodev,allow_other,blksize=4096)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/peter/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=peter)

fstab contains
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=959cb526-06f8-4d5d-bec2-a6b42f438b07 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=e56dad6b-358f-4948-b51f-4abce81f50b1 none            swap    sw              0       0
/dev/sdb1 /media/Win-Storage ntfs-3g defaults,user,locale=en_GB.utf8 0 0
/dev/sdc1 /media/Win-MyDocs ntfs-3g defaults,user,locale=en_GB.utf8 0 0
# /dev/sdd1 /media/Win-Video ntfs-3g defaults,user,locale=en_GB.utf8 0 0

I had to comment sdd1 out as it's causing problems on bootup, it used to work.

I'm stumped. Anyone help?

---

### Post by pooky2483 on 2011-11-13
Sorted it.

---

