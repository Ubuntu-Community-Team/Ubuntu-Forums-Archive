---
title: "[SOLVED] Can't mount a disk"
date: 2008-11-09
forum: General Help
---

### Post by kextyn on 2008-11-09
I just installed 8.10 Server AMD64 and everytime I try to mount this one partition it says it's already mounted or the mount point is busy.  I have tried making different mount points with no success and the device isn't already mounted.

The partition I'm having problems with is /dev/sdb1 although sometimes it'll show up as /dev/sdi1 because Ubuntu still seems to enjoy switching my controllers around randomly.  /dev/md0 mounts just fine and I mounted that just before I tried to mount /dev/sdb1 the first time.  I should also mention that before installing 8.10 I ran the livecd and copied /dev/sda1 to /dev/sdb1 (it's my 8.04 installation that got screwed up) then I deleted /sda1 and installed 8.10.

mount
```

/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
securityfs on /sys/kernel/security type securityfs (rw)
/dev/md0 on /raid type ext3 (rw)
```

fdisk -l
```

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe9b26c37

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        9327    74919096   83  Linux
/dev/sda2            9328        9729     3229065    5  Extended
/dev/sda5            9328        9729     3229033+  82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x96d54bb4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9327    74919096   83  Linux

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000e2bd8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        9730    78148608    7  HPFS/NTFS

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0002b2a7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       60801   488384001   fd  Linux raid autodetect

Disk /dev/sde: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00078814

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1       60801   488384001   fd  Linux raid autodetect

Disk /dev/sdf: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000eaae1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1   *           1       60801   488384001   fd  Linux raid autodetect

Disk /dev/sdg: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000e3e8d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1               1       60801   488384001   fd  Linux raid autodetect

Disk /dev/sdh: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000a9683

   Device Boot      Start         End      Blocks   Id  System
/dev/sdh1               1       60801   488384001   fd  Linux raid autodetect

Disk /dev/sdi: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0008a179

   Device Boot      Start         End      Blocks   Id  System
/dev/sdi1               1       60801   488384001   fd  Linux raid autodetect

Disk /dev/sdj: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x68eea170

   Device Boot      Start         End      Blocks   Id  System
/dev/sdj1               1       60801   488384001   fd  Linux raid autodetect


```

/etc/fstab
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=4cf1ec94-60df-4e01-ad87-258ccb3c9251 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=20d366a0-e8ef-433e-91e2-c72bf7494c7c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
# /dev/md0
/dev/md0        /raid   ext3    defaults        0       0
# /dev/sdb1
/dev/sdb1       /clone  ext3    defaults        0       0

```

---

### Post by taurus on 2008-11-09
What's the output of 

```
ls -la /dev/disk/by-uuid
```

---

### Post by kextyn on 2008-11-09
I didn't even think about adding the options to ls /dev/disk/by-uuid/  I just did that and had a list of UUIDs and hadn't gotten around to doing anything with them.

```

total 0
drwxr-xr-x 2 root root 140 2008-11-09 21:50 .
drwxr-xr-x 5 root root 100 2008-11-09 21:50 ..
lrwxrwxrwx 1 root root   9 2008-11-09 21:50 0eb7cbf6-b3df-4359-857b-8fdb91174739 -> ../../md0
lrwxrwxrwx 1 root root  10 2008-11-09 21:50 20d366a0-e8ef-433e-91e2-c72bf7494c7c -> ../../sda5
lrwxrwxrwx 1 root root  30 2008-11-09 21:50 3d79ff63-6efe-448b-816a-1db36adfd8a0 -> ../../mapper/sil_agbgagddaecb1
lrwxrwxrwx 1 root root  10 2008-11-09 21:50 4cf1ec94-60df-4e01-ad87-258ccb3c9251 -> ../../sda1
lrwxrwxrwx 1 root root  10 2008-11-09 21:50 5CF67446F6742306 -> ../../sdc1

```

Is it something to do with that mapper one?

---

### Post by drs305 on 2008-11-09
Have you tried changing the fstab device ID to uuid rather than /dev/sdb1? Even if that doesn't correct the immediate problem it would take care of the 'changing' device identifier in the future (sdb1 one day, sdi1 the next). You can get the unmounted uuid with "sudo blkid" if it's not one of the ones listed above (with a new /dev designation).

fstab entry:
```

# /dev/sdb1
uuid=xxxxxx  /clone  ext3    defaults,user   0   0
```

Is the fsck code 0 rather than 2 because you are running a server?

---

### Post by kextyn on 2008-11-09
It works when I use the UUID for ../../mapper/sil_agbgagddaecb1.  How can I get that to show up as the normal /dev/sdb1?

---

### Post by kextyn on 2008-11-09
> **drs305 said:**
> 
Is the fsck code 0 rather than 2 because you are running a server?

Honestly, I'm not sure.  I'm assuming you're talking about the 0's in the fstab.  I've always just used zeroes there with no issues.

---

### Post by drs305 on 2008-11-09
The last digit in the fstab line tells the system if it should periodically check the partition with fsck. The root partition is normally 1, other ext2/3 partitions are  usually 2 (lower) priority than root, and non-linux partitions are set to 0 since fsck doesn't check them.

I believe the default period between checks is 30 mounts (don't quote me). If you reboot very often or seldom, you may want to change that to something else. You can use mounts, days, etc and it is configurable with the tune2fs command. You can read the tune2fs man page if you want to learn which switches to use.

As for the mount, you might just be able to use the mappers uuid if it correctly identifies what you think is sdb1. You can make the mount point anything you want. To be honest, if you use the uuid and it works it doesn't really matter what the device is actually called since linux uses mount points and you can name the mount point anything you want to. 

You could also label the device to a more reasonable name, again using tune2fs. The label could be used in fstab instead of the uuid if you prefer.

---

### Post by kextyn on 2008-11-10
Well I'm assuming the partition has that crazy name because I copied another partition.  It's not a big issue to me because I'll probably be repartitioning it as soon as I know my system is stable.  So I'll just use the UUID for now.

My server rarely gets restarted so the drives wouldn't get checked anyway.  I'll look into setting it to check every # days or something though.

Thanks for the help guys. :)

---

