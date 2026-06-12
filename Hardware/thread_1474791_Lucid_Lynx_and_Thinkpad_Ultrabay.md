---
title: "Lucid Lynx and Thinkpad Ultrabay"
date: 2010-05-06
forum: Hardware
---

### Post by bomanizer on 2010-05-06
Hi, I got this weird behavior on my T61:

When I boot with a HDD sitting in the ultrabay, mtab, shows the system disk as sdb1, whereas fstab states sda1. I added an entry to fstab to mount the ultrabay HDD on boot, but it fails to do so. Here are some relevant snipplets:

```
janne@shazam:~$ cat /etc/mtab
/dev/sdb1 / ext4 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
none /sys sysfs rw,noexec,nosuid,nodev 0 0
none /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
none /dev devtmpfs rw,mode=0755 0 0
none /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
none /dev/shm tmpfs rw,nosuid,nodev 0 0
none /var/run tmpfs rw,nosuid,mode=0755 0 0
none /var/lock tmpfs rw,noexec,nosuid,nodev 0 0
none /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0
none /var/lib/ureadahead/debugfs debugfs rw,relatime 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/janne/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=janne 0 0
janne@shazam:~$ cat /etc/fstab 
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
/dev/sdb1	/media/ultrabay	ext3	errors=remount-ro	0	1
# swap was on /dev/sda5 during installation
UUID=780fbe00-6580-46a3-8cd3-90865c13d4e0 none            swap    sw              0       0

```

and boot.log:

```
fsck from util-linux-ng 2.17.2

fsck from util-linux-ng 2.17.2

/dev/sdb1: clean, 179838/7028736 files, 11639259/28103168 blocks

/dev/sdb1: clean, 179838/7028736 files, 11639259/28103168 blocks

mount: /dev/sdb1 already mounted or /media/ultrabay busy

mount: according to mtab, /dev/sdb1 is mounted on /

mountall: mount /media/ultrabay [832] terminated with status 32

mountall: Filesystem could not be mounted: /media/ultrabay

Skipping /media/ultrabay at user request
```

what's going on?

Thanks.

---

