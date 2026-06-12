---
title: "Missing disk space"
date: 2008-08-07
forum: General Help
---

### Post by Wastedyouthfx0 on 2008-08-07
Hello,

Yesterday I lost a hard drive in my computer, and it was a dedicated drive for my home partition.  I already had an identical drive in my computer, so I was able to relocate and copy what a could over to the new drive and point the /home to the new drive.

While copying files to the new drive, I ran out of disk space... which is odd because they are identical sizes. 

```
root@shadow:/etc# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             176G  9.3G  158G   6% /
varrun                1.5G  260K  1.5G   1% /var/run
varlock               1.5G     0  1.5G   0% /var/lock
udev                  1.5G   60K  1.5G   1% /dev
devshm                1.5G   12K  1.5G   1% /dev/shm
/dev/sdb1             232G  197G   24G  90% /home

``` 

The drive with the problem is /dev/sdb1 (I removed the other drive because it smells like its about ready to catch on fire).  It says that 197G are being used.  But, the disk analyzer says I'm only using 112.2G.  Right clicking on the home folder and selecting properties only shows 87.6G worth of files.  

What's going on!?!  I'm missing half my drive space?!

I unmounted the drive and forced an e2fsck but it didn't find any problems

fstab

```
root@shadow:/etc# more fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=b3045d4b-c9cd-49b6-8dbe-7478703a8a75 /               ext3    errors=remount-ro 0       1
# /dev/hda5
UUID=e6c0c3d6-948b-4943-8457-127c384c02c4 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
#/dev/sdc1 	/home 		ext3 defaults,errors=remount-ro 0 1
UUID=1966839c-6e88-47eb-b037-f97ab9ce165b /home ext3 defaults,errors=remount-ro 0 1
#/dev/sda1	/media/disk	ext3 defaults,errors=remount-ro 0 1
#UUID=4155fe14-c3ce-440b-ae93-fda3d6a566ec /home ext3 defaults,errors=remount-ro 0 1

```

mtab
```
root@shadow:/etc# more mtab
/dev/sda1 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
/dev/sdb1 /home ext3 rw,errors=remount-ro 0 0
securityfs /sys/kernel/security securityfs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/djp/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=djp 0 0
/dev/sdc1 /media/My\040Passport vfat rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush 0 0

```

---

