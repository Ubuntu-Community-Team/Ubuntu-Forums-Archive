---
title: "Issues resizing parition"
date: 2009-08-30
forum: Hardware
---

### Post by Grimshawlogic on 2009-08-30
Very new to linux I partitioned the HD on a new laptop and set up a triple boot to play around with it -originally Vista which I kept on one partition for running new versions of MS programs, XP installed on another partition for old MS programs, ubuntu 8.04 on another partition, 2 partitions left by Dell I kept because they were small and I didn't know much about them, a partition for swap and a partition for data as follows:
(200gb drive)
Primaries: 
/dev/sda1 fat16 DellUtility
/dev/sda2 ntfs Xp
/dev/sda3 ntfs vista
Extended(/dev/sda4 115.67GiB):
/dev/sda5 ntfs Data
(some *previously?* unallocated space) 
/dev/sda6 ext3 Ubuntu 
/dev/sda7 linux-swap Swap
(more unallocated space)
/dev/sda8 fat32 Mediadirect(Dell)

anyway, sda5, Data was originally ~70 GiB, but I had almost filled both the windows partitions and the 'data' partition, so I figured I'd grow 'Data' into the unallocated space next to it and clean up the Windows partitions. So I enlarged it to 102 GiB. It seemed ok but once I started moving files data's capacity capped around 70 and gave me errors saying it couldn't take anymore. (Btw I did all the partition editing with GParted and was moving files in Windows). When I checked the drive in the 'computer' folder in vista the drive showed 100GiB. In 'properties' it had the old size though. So I checked it out in Ubuntu (9.04). When I opened GParted I'm shown a message:
"The kernel is unable to re-read the partition tables on the following devices:
- /dev/sda

Because of this you will only have limited access to these devices. Unmount all mounted partitions on a device to get full access."
It opens and sda5, the data partition is flagged with a <!> and in info:
"Warning: the device /dev/sda5 doesn't exist

ntfsresize v2.0.0(libntfs 10:0:0)
ERROR(2):Failed to check '/dev/sda5' mount state: No such file or directory. Probably /etc/mtab is missing. It's too risky to continue. You might try another Linux distro. 

Unable to read the contents of this file system!
Because of this some operations may be unavailable"

I'm totally lost, when I reboot to windows the drive reads and works normally as though it is 70GiB (past that there are still errors though). I could back everything up and flatten it but I'd really rather not. Anybody know how I may properly resize this partition/ fix these errors? GParted isn't letting me do much now in this state and I don't have another distro to try. (I'm also not sure what information might be relevant, so ask away, when I look in /etc/mtab there *is* actually a file if that helps:

proc /proc proc rw 0 0
sysfs /sys sysfs rw 0 0
tmpfs /lib/modules/2.6.28-11-generic/volatile tmpfs rw,mode=0755 0 0
tmpfs /lib/modules/2.6.28-11-generic/volatile tmpfs rw,mode=0755 0 0
tmpfs /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0
varrun /var/run tmpfs rw,nosuid,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
tmpfs /dev/shm tmpfs rw,nosuid,nodev 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=620 0 0
rootfs / rootfs rw 0 0
/dev/sr0 /cdrom iso9660 ro,noatime 0 0
/dev/loop0 /rofs squashfs ro,noatime 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0
tmpfs /tmp tmpfs rw,nosuid,nodev 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/ubuntu/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=ubuntu 0 0

)

---

### Post by Paul Crawford on 2010-05-13
Were you doing this from a boot CD / USB stick or while running 'live' from the disk?

I normally avoid re-sizing the physical disk the system is running from just in case, even if the partition in question is not mounted.

---

### Post by 2hot6ft2 on 2010-05-13
> **Paul Crawford said:**
> Were you doing this from a boot CD / USB stick or while running 'live' from the disk?

I normally avoid re-sizing the physical disk the system is running from just in case, even if the partition in question is not mounted.
I hope you're not sitting around refreshing this expecting an answer from the OP as it was posted in August of 2009 and the OP has not made any other posts since then.
:lolflag:

---

