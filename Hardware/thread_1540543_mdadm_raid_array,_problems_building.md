---
title: "mdadm raid array, problems building"
date: 2010-07-27
forum: Hardware
---

### Post by ktikley on 2010-07-27
Okay, for starters, let me begin by saying I'm a total Linux noob. Please be gentle.

I'm having problems building a raid array using mdadm.  This is an array that had been a fake raid device on my old windows OS.  I didn't care about any of the data, and since many posts I had read about getting raid to work on ubuntu said soft raid was generally easier and better anyways, I just tore it down and decided to rebuild it.

I want to use this array as a striped array for my home folder (I never save anything super critical, and this isn't like a server or anything, I'm willing to live on the edge.)  So I want this to be mounted at boot.  After playing with it a little bit, I got it to work, but I couldn't get it to mount at boot. One guide ([http://bfish.xaedalus.net/2006/11/software-raid-5-in-ubuntu-with-mdadm/](http://bfish.xaedalus.net/2006/11/software-raid-5-in-ubuntu-with-mdadm/)) is great, but made me want to just try again from the beginning, since I was already pretty frustrated with it at this point.  However, still can't get it to boot for some reason.

It seems like my earlier tinkering with it made it so I can't format the entire drive, and that mdadm and gparted both seem to recognize the second drive as part of a previous array (which is was I suppose for a short time.)  And disk utility shows 2(!) raid arrays available:
[[IMG]http://img571.imageshack.us/img571/8866/scrn1.th.png[/IMG]]("http://img571.imageshack.us/i/scrn1.png/")

[U][[IMG]http://img23.imageshack.us/img23/5272/scrn2.th.png[/IMG]]("http://img23.imageshack.us/i/scrn2.png/")
[/U]
(Oh yeah, and that misalignment thing. Would be happy to fix that, but low on the list of priorities.)

Any help would be greatly appreciated with this.

Here's what most people seem to be asking for whenever I searched for mdadm posts:

```
fdisk -l
Disk /dev/sda: 32.0 GB, 32017047552 bytes
255 heads, 63 sectors/track, 3892 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000714cf

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3727    29931520   83  Linux
/dev/sda2            3727        3893     1332225    5  Extended
/dev/sda5            3727        3893     1332224   82  Linux swap / Solaris

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00003a19

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001   fd  Linux raid autodetect

Disk /dev/sdc: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00043d9c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       30401   244196001   fd  Linux raid autodetect

Disk /dev/md0: 500.1 GB, 500113211392 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 65536 bytes / 131072 bytes
Disk identifier: 0x000bcf4d

    Device Boot      Start         End      Blocks   Id  System
/dev/md0p1               1       60801   488384001   83  Linux
Partition 1 does not start on physical sector boundary.

``````
cat /etc/mdadm/mdadm.conf
DEVICE partitions
ARRAY /dev/md0 level=raid0 num-devices=2 metadata=00.90 UUID=d6a9f7c8:8cf2a351:4be2e130:860764f4

```

---

### Post by jacekk015 on 2010-07-28
Give results of:
```
cat /etc/mtab
and
cat /etc/fstab
```We will see then what supposed to be mounted on boot.


About creating/removing RAID and etc.
If you destroy RAID on disk still remain superblock.
If you want to fully destroy information after destroy raid use:
```
mdadm --zero-superblock /dev/sdX
```[http://linux.die.net/man/8/mdadm](http://linux.die.net/man/8/mdadm)

---

### Post by ktikley on 2010-07-28
Here they go:

```
cat /etc/mtab
/dev/sda1 / ext4 rw,errors=remount-ro 0 0
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
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/kevin/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=kevin 0 0

```and...

```
cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=503382e3-2185-4222-9457-0341948759a9 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=55a51042-7d11-4079-a6d1-949552483e3b none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0      0
/dev/md0     /var/media     auto     defaults     0     3 

```That bottom one in fstab was one I edited in (per the guide I was following.)  Should I start over again and try to zero the super block this time?

---

### Post by jacekk015 on 2010-07-28
From the /cat/fstab looks that you don't have really installed Ubuntu on this RAID1 array.

You have installed root partition [/] on the sda1 - that's first partition of sda disk
SWAP partition is on sda5.

Give result of:
```
sudo mdadm --detail /dev/md0
```It will show what disks/partitions you have connect to this array.

---

### Post by ktikley on 2010-07-29
That'd be correct, I have the OS on the SSD (sda1), and the RAID array is for the home folder/files.

mdadm --detail:
```
mdadm: metadata format 00.90 unknown, ignored.
/dev/md0:
        Version : 00.90
  Creation Time : Tue Jul 27 14:59:02 2010
     Raid Level : raid0
     Array Size : 488391808 (465.77 GiB 500.11 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Tue Jul 27 14:59:02 2010
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

     Chunk Size : 64K

           UUID : d6a9f7c8:8cf2a351:4be2e130:860764f4
         Events : 0.1

    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       8       33        1      active sync   /dev/sdc1

```

---

### Post by jacekk015 on 2010-07-29
Look on your fdisk -l result. You should mount in fstab:
```
/dev/md0p1
```First partition of your md0 device.

---

### Post by ktikley on 2010-07-29
Just edited the last line in fstab to /dev/md0p1 and restarted. Still get the message "Disk in /dev/media not ready or not present. Continue to wait; Press S to continue...."

---

### Post by jacekk015 on 2010-07-29
Similar problems are here
[http://ubuntuforums.org/showthread.php?t=1484148](http://ubuntuforums.org/showthread.php?t=1484148)

There is something wrong in you fstab string:
<file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/md0     /var/media ext432 auto 0 2
OR
/dev/md0p1     /var/media ext432 auto 0 2

Change ext432 to you formatted file system.

I think that your /var/media is also wrong point.
Doesn't should be /media/something or /mnt/something?
Above you are writing /dev/media !

---

### Post by ktikley on 2010-07-30
Yeah, /dev/media was a typo, it was meant to be /var/media.

Got it working though, this is all I did:

zero'd the superblock on both disks, mdadm output said something similar to version 00.90 ignored or something (sorry, should've saved it.)

G'parted the array to ext3. After it finished formatting, the mount point was listed as /var/media.  Crossed my fingers and rebooted, and this time no error message on the boot screen, and when I go to /var/media says 435 GB available.  This whole mount point thing is a little confusing to me still, but it appears to be working.

Now I think I'll move my home folder on over and see how it goes. :P

Thanks for all your help!

---

### Post by jacekk015 on 2010-07-30
00.90 is the RAID metadata version.

Take in mind that you have RAID0, and your data will fly away with first broken disk drive.

I'm glad it finally works.

---

