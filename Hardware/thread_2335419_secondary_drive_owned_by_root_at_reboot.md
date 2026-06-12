---
title: "secondary drive owned by root at reboot"
date: 2016-08-28
forum: Hardware
---

### Post by netopalis45 on 2016-08-28
Lately whenever I reboot my secondary drive is owned by root. This drive has my home folder so I then have to take ownership of the drive and re-link the drive to my home folder and fix all my settings. Since it has a different owner every time, it has a different name every reboot as well. For example, drive is named Extended but when I reboot it changed to Extended1. I have had to reboot several times since this started happening and it has iterated every time since (Extended2, Extended3, Extended4 and so forth). How can I make sure that the drive is owned by me and not root at startup?

---

### Post by Bashing-om on 2016-08-28
netopalis45; Hello;

That authorization access depends on the file system that is used on this secondary device.
Show us what we are working with:
```

sudo blkid -c /dev/null -o list
sudo fdisk -lu
sudo parted -l
cat /etc/fstab
cat /proc/mounts

```
and we see what the file system is, how it is presently mounting, and what we can do to change the mount options.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by netopalis45 on 2016-08-28
sudo blkid -c /dev/null -o list
```
/dev/sdb ext4 Extended /media/josh/Extended6
```

sudo fdisk -lu
```
Disk /dev/sdb: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
```

sudo parted -l
```
Model: ATA ST1000DM003-9YN1 (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: loop
Disk Flags: 


Number  Start  End     Size    File system  Flags
 1      0.00B  1000GB  1000GB  ext4
```

cat /etc/fstab
```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdb2 during installation
UUID=53d63495-86c8-4665-9413-9b7c05c29b5c /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sdb1 during installation
UUID=30D6-C689  /boot/efi       vfat    umask=0077      0       1
# swap was on /dev/sdb3 during installation
UUID=b488e12d-2edd-423a-a79f-03528cb39e1a none            swap    sw              0       0
```

cat /proc/mounts
```
sysfs /sys sysfs rw,nosuid,nodev,noexec,relatime 0 0
proc /proc proc rw,nosuid,nodev,noexec,relatime 0 0
udev /dev devtmpfs rw,nosuid,relatime,size=3011632k,nr_inodes=752908,mode=755 0 0
devpts /dev/pts devpts rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000 0 0
tmpfs /run tmpfs rw,nosuid,noexec,relatime,size=606184k,mode=755 0 0
/dev/sda2 / ext4 rw,relatime,errors=remount-ro,data=ordered 0 0
securityfs /sys/kernel/security securityfs rw,nosuid,nodev,noexec,relatime 0 0
tmpfs /dev/shm tmpfs rw,nosuid,nodev 0 0
tmpfs /run/lock tmpfs rw,nosuid,nodev,noexec,relatime,size=5120k 0 0
tmpfs /sys/fs/cgroup tmpfs ro,nosuid,nodev,noexec,mode=755 0 0
cgroup /sys/fs/cgroup/systemd cgroup rw,nosuid,nodev,noexec,relatime,xattr,release_agent=/lib/systemd/systemd-cgroups-agent,name=systemd 0 0
pstore /sys/fs/pstore pstore rw,nosuid,nodev,noexec,relatime 0 0
efivarfs /sys/firmware/efi/efivars efivarfs rw,nosuid,nodev,noexec,relatime 0 0
cgroup /sys/fs/cgroup/cpu,cpuacct cgroup rw,nosuid,nodev,noexec,relatime,cpu,cpuacct 0 0
cgroup /sys/fs/cgroup/cpuset cgroup rw,nosuid,nodev,noexec,relatime,cpuset 0 0
cgroup /sys/fs/cgroup/memory cgroup rw,nosuid,nodev,noexec,relatime,memory 0 0
cgroup /sys/fs/cgroup/blkio cgroup rw,nosuid,nodev,noexec,relatime,blkio 0 0
cgroup /sys/fs/cgroup/pids cgroup rw,nosuid,nodev,noexec,relatime,pids 0 0
cgroup /sys/fs/cgroup/freezer cgroup rw,nosuid,nodev,noexec,relatime,freezer 0 0
cgroup /sys/fs/cgroup/net_cls,net_prio cgroup rw,nosuid,nodev,noexec,relatime,net_cls,net_prio 0 0
cgroup /sys/fs/cgroup/hugetlb cgroup rw,nosuid,nodev,noexec,relatime,hugetlb 0 0
cgroup /sys/fs/cgroup/perf_event cgroup rw,nosuid,nodev,noexec,relatime,perf_event 0 0
cgroup /sys/fs/cgroup/devices cgroup rw,nosuid,nodev,noexec,relatime,devices 0 0
systemd-1 /proc/sys/fs/binfmt_misc autofs rw,relatime,fd=33,pgrp=1,timeout=0,minproto=5,maxproto=5,direct 0 0
mqueue /dev/mqueue mqueue rw,relatime 0 0
debugfs /sys/kernel/debug debugfs rw,relatime 0 0
hugetlbfs /dev/hugepages hugetlbfs rw,relatime 0 0
fusectl /sys/fs/fuse/connections fusectl rw,relatime 0 0
/dev/sda1 /boot/efi vfat rw,relatime,fmask=0077,dmask=0077,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,relatime 0 0
tmpfs /run/user/1000 tmpfs rw,nosuid,nodev,relatime,size=606184k,mode=700,uid=1000,gid=1000 0 0
/dev/sdc1 /media/josh/Seagate fuseblk rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096 0 0
/dev/sdb /media/josh/Extended6 ext4 rw,nosuid,nodev,relatime,data=ordered 0 0
tmpfs /run/user/108 tmpfs rw,nosuid,nodev,relatime,size=606184k,mode=700,uid=108,gid=114 0 0
gvfsd-fuse /run/user/1000/gvfs fuse.gvfsd-fuse rw,nosuid,nodev,relatime,user_id=1000,group_id=1000 0 0
```

Not much of that makes any sense to me but hopefully it helps

---

### Post by Bashing-om on 2016-08-28
netopalis45; Welllll ..

Not enouggh info to make much sense of this either.
In the command " sudo blkid -c /dev/null -o list " I would expect something similar to my output:
> 
sysop@1404mini:~$ sudo blkid -c /dev/null -o list
[sudo] password for sysop: 
device       fs_type label    mount point      UUID
-----------------------------------------------------------------------------------
/dev/sda1    ext4    1404mroot /               3a47f1f1-ed1f-4134-b6aa-be101a7d97b4
/dev/sda2    ext4    1404mhome /home           29a6fc4f-ff12-4cac-8eb1-e98e50f1107f
/dev/sda5    swap             <swap>           192a4783-56fa-4fd0-a62f-c45a14c08482
/dev/sda6    ext4    DATA     (not mounted)    3ad091a1-5036-463b-ba4e-88e98e41b07a
/dev/sda7    ext4    LUBU1404 (not mounted)    4e6cd96d-49bd-47f0-9dfe-8eeebad4cf9d
/dev/sda8    ext4    1404mvar /var             136af805-5758-4880-acc4-0e1d35e2c266
/dev/sdb1    ext4    ubie14.04std (not mounted) 345cab2e-22e7-4f89-8781-05cc0f7628a2
/dev/sdb2    ext4    ubie1204 (not mounted)    7dd23297-30ea-417a-8f69-3e2df76f3192
/dev/sdb3    ext4    ubie1604 (not mounted)    2ec4733f-db40-4db0-aef8-5c54e54085ab
sysop@1404mini:~$

( here where my data drives are NOT explicitly mounted ) 

But I am in some measure of distress in that the file system on the sdb drive is reported as:
> 
Partition Table: loop

where I had expected a file system type of msdos or GPT . I do not know what "loop" implies !

As the drive is not automounted in fstab; are you UNmounting (safely) that secondary drive prior to shutting down/rebooting the system ?? 

While I am dithering about .. what have we for established mount points ? looks like presently you are depending on gvfs to make that secondary drive available.
Post back:
```

gvfs-mount --list
ls -al /media/josh

```
be aware I can accept that " The program 'gvfs-mount' is currently not installed " in this instance.

[INDENT][INDENT]maybe one of those times
[INDENT][INDENT][INDENT]I don a learning cap
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

