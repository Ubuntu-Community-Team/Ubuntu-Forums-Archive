---
title: "Problems with new Partition"
date: 2007-06-16
forum: Hardware &amp; Laptops
---

### Post by gwm123 on 2007-06-16
Hi, I just added another partition to my hard drive. The computer gives me an error message that says "Error while copying to /media/disk" new line "You do not have permissions to write this folder." I can't figure out why it is doing this. Here is my fstab file: 

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=591e90ec-385b-4b0e-b3e9-93368863e42a /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=7e8dc75e-c88a-4d5c-8b32-927ea0820e58 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

----------------------- my sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         182     1461883+  82  Linux swap / Solaris
/dev/sda2             183        2188    16113195   83  Linux
/dev/sda3            2189        8409    49970182+  83  Linux


Thanks,
George

---

### Post by merlinus on 2007-06-16
sda3 is not listed in /etc/fstab.  I assume that this is your new partition???

Did you try to mount it manually?  If so, how did you attempt to do this?

Did you try re-booting?

-merlin

---

### Post by IntuitiveNipple on 2007-06-16
What does mount report?
```
$ mount
```
Because the disk is fixed (not removable) even if the partition is mounted manually it is probable a regular user won't have permissions to write to it since by default fixed disks are mounted by root and have ownership root:root and permission rwx r-x r-x (owner, group, all).

You many need to add an entry to fstab for the new partition with the option **user** in place of **defaults**.

You may also need to check and change the ownership and permissions of the mount-point in /media/ but, as I notice you referred to it as "disk" I am guessing it was auto-mounted by gnome-vfs in which case the "disk" directory is created by gnome rather than manually.

---

### Post by gwm123 on 2007-06-16
here is what the mount command gives me:

/dev/sda2 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-16-generic/volatile type tmpfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/scd0 on /media/cdrom0 type iso9660 (ro,noexec,nosuid,nodev,user=gmelcer)
/dev/sda3 on /media/disk type ext3 (rw,noexec,nosuid,nodev)


I have not tried to mount this partition manually. How would I do that?

---

### Post by IntuitiveNipple on 2007-06-16
> **gwm123 said:**
> here is what the mount command gives me:

/dev/sda3 on /media/disk type ext3 (rw,noexec,nosuid,nodev)

As I thought, it has been automounted on /media/disk/. I'm guessing if you check ownership and permissions on that you'll find it is owned by root and will look something like this:
```
$ ls -ld /media/disk
drwxr-xr-x 2 root root  4096 2007-05-19 17:01 disk
```
In which case you should follow my previous suggestion and add an entry into /etc/fstab for it with a mount-point that allows users to write to it.

First unmount the current disk:
```
$ sudo umount /media/disk
```
This code should automatically add the required line to /etc/fstab for you:
```
$ sudo vol_id /dev/sda3 | sudo awk 'BEGIN { FS="="; } { if($0 ~ /^ID_FS_UUID/) { print("#/dev/sda3\nUUID=" $2 " /media/sda3 ext3 rw,user 0 1") >> "/etc/fstab"; } }'
```
Check /etc/fstab, it should have something similar to this at the end (the UUID will be different):
```
#/dev/sda3
UUID=e5eb4b0d-f98b-4ab6-b1a8-0e2bd9ecc4dd /media/sda3 ext3 rw,user 0 1
```
Now create the mount-point and set its ownership:
```
$ sudo mkdir /media/sda3
$ sudo chown ${USERNAME}:users /media/sda3
```
And try mounting it:
```
$ mount /dev/sda3
$ ls /media/sda3
```

---

### Post by gwm123 on 2007-06-16
Still giving me the same problem. It seems like the partition is mounted with the right permissions.  Is there something I missed?

mount:

/dev/sda2 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-16-generic/volatile type tmpfs (rw)
/dev/sda3 on /media/sda3 type ext3 (rw,noexec,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/scd0 on /media/cdrom0 type iso9660 (ro,noexec,nosuid,nodev,user=gmelcer)
/dev/sdb2 on /media/GEORGE W type vfat (rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077)

------------------------fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=591e90ec-385b-4b0e-b3e9-93368863e42a /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=7e8dc75e-c88a-4d5c-8b32-927ea0820e58 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
#/dev/sda3
UUID=2b7973cb-39ce-4070-a166-232ac0aec3d5 /media/sda3 ext3 rw,user 0 1


----------------------fdisk

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         182     1461883+  82  Linux swap / Solaris
/dev/sda2             183        2188    16113195   83  Linux
/dev/sda3            2189        8409    49970182+  83  Linux

---

