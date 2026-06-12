---
title: "Mount problems on NTFS disk"
date: 2012-02-10
forum: Hardware
---

### Post by patman0623 on 2012-02-10
I am unable to mount a partition on a disk, and I don't know why. The operating system is reporting erroneously that the disk is in use. 

Here is the output:
> $ $ sudo mount /dev/sda2 disk
$ sudo umount disk
$ sudo mount /dev/sda3 disk
mount: /dev/sda3 already mounted or disk busy
$ lsof /dev/sda3
$ fuser /dev/sda3

Notice that neither lsof nor fuser is reporting the disk is in use. It works if I try sda2, but not sda3. I have tried rebooting the computer twice, including a removal of existing mount partitoins in /etc/fstab, to no avail. This is very frustrating because I promised a customer I would copy her data very soon, but I can't because the the disk won't mount.

Here is a copy of my mount command:
> $ sudo mount
/dev/sdb6 on / type ext4 (rw,errors=remount-ro,commit=0)
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
/dev/sdb4 on /mnt/windows-backup type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/home/patrick/.Private on /home/patrick type ecryptfs (ecryptfs_check_dev_ruid,ecryptfs_cipher=aes,ecryptfs_key_bytes=16,ecryptfs_unlink_sigs,ecryptfs_sig=*removed*,ecryptfs_fnek_sig=*removed*)
gvfs-fuse-daemon on /home/patrick/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=patrick)
/dev/sdb2 on /mnt/windows type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)


---

### Post by ahallubuntu on 2012-02-10
What's the output of

sudo fdisk -l /dev/sda

?

---

### Post by patman0623 on 2012-02-10
> $ sudo fdisk -l /dev/sda
[sudo] password for patrick: 

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x40000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63      112454       56196   de  Dell Utility
/dev/sda2   *      112640    27641855    13764608    7  HPFS/NTFS/exFAT
/dev/sda3        27641856  1250260991   611309568    7  HPFS/NTFS/exFAT
 
.

---

### Post by dabl on 2012-02-10
Try a

```
sudo umount /dev/sda3
```

and post any error output.

Is there a chance that this partition was not cleanly closed by Windows?  Are you able to boot Windows and chkdsk it?

---

