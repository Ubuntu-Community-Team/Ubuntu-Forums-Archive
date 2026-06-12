---
title: "dvd rom will not mount"
date: 2009-12-29
forum: Hardware
---

### Post by gordon3913 on 2009-12-29
Using Ubuntu 9.10 my dvd drive will not mount
It is coming up on my Places list as cdrom0
When I tried to run a cd or dvd it came up with the message can't find /dev/scdo - I created that directory but it came up with that it was not a block device.
When I tried to mount it from the command line I got 
"can't find cdrom0 in /etc/fstab or /etc/mtab"

Below is my fstab listing
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda3 during installation
UUID=7ff57d03-4560-4660-b5de-95c25dd1d185 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda4 during installation
UUID=3071c7d5-9a72-4257-be35-cc59b4149590 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

Can some please help

---

### Post by gordon3913 on 2009-12-29
mtab file has no cdromO device

/dev/sda3 / ext4 rw,errors=remount-ro 0 0
proc /proc proc rw 0 0
none /sys sysfs rw,noexec,nosuid,nodev 0 0
none /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
udev /dev tmpfs rw,mode=0755 0 0
none /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
none /dev/shm tmpfs rw,nosuid,nodev 0 0
none /var/run tmpfs rw,nosuid,mode=0755 0 0
none /var/lock tmpfs rw,noexec,nosuid,nodev 0 0
none /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/gordon/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=gordon 0 0

---

