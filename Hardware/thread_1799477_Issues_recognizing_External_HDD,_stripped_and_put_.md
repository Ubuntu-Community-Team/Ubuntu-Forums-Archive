---
title: "Issues recognizing External HDD, stripped and put into PC."
date: 2011-07-07
forum: Hardware
---

### Post by anotheraddict on 2011-07-07
Hey guys, I'm getting the following error after trying to take my external Seagate Deskagent apart and installing it as a stand alone, internal drive.  

```
[INDENT]Error mounting: mount exited with exit code 1: helper failed with:
mount: according to mtab, /dev/sdb1 is already mounted on /
mount failed
[/INDENT]
```

My mtab reads:
```
[INDENT]/dev/sdb1 / ext4 rw,errors=remount-ro,commit=0 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
none /sys sysfs rw,noexec,nosuid,nodev 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
none /dev devtmpfs rw,mode=0755 0 0
none /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
none /dev/shm tmpfs rw,nosuid,nodev 0 0
none /var/run tmpfs rw,nosuid,mode=0755 0 0
none /var/lock tmpfs rw,noexec,nosuid,nodev 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
/home/another/.Private /home/another ecryptfs ecryptfs_cipher=aes,ecryptfs_key_bytes=16,ecryptfs_unlink_sigs,ecryptfs_sig=852fca49d18152ca,ecryptfs_fnek_sig=81a2c79e97d73c8a 0 0
gvfs-fuse-daemon /home/another/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=another 0 0
/dev/sdc1 /media/Games fuseblk rw,nosuid,nodev,allow_other,blksize=4096,default_permissions 0 0[/INDENT]
```

And Fstab:
```
[INDENT]# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
#UUID=667fa044-0b40-4ac5-8062-4574fe905f09 none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0[/INDENT]
```

Basically I had the HDD working as a emulated internal drive with windows 7, and before I made the decision to migrate to Ubuntu (actually Mint 11) I decided I would take that external and move it internally as I had no use for the portability.

Thanks for the taking the time to help, I'm at a loss without my data! (literally every bit of my entertainment :icon_frown:)

---

### Post by anotheraddict on 2011-07-07
Also, if it is relevant, the drive is NTFS format.  And i'm seeking to preserve the data on said drive.

---

