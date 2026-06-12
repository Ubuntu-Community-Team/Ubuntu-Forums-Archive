---
title: "Resize partition did not resize properly"
date: 2009-08-11
forum: Installation &amp; Upgrades
---

### Post by ubantuwannabe on 2009-08-11
Dear all,

I have a 320G hard disk.

Here the original partition:

first partition ntfs  windows xp (occupies almost 318G if I din remember wrongly)
second partition fat32 for recovery partition (occupies 2G for recovery options)


I wanted to achieve the following:

first partition ntfs to install windows xp
second partition fat32 for recovery partition
third partition ubuntu 8.10

first I defrag the first partition.

next I resize the partition during the installation of ubuntu 8.10
using the first option guided resize option as shown in [http://launchpadlibrarian.net/18301624/screenshot_fail.png](http://launchpadlibrarian.net/18301624/screenshot_fail.png).

(Note the above is not my screenshot, but it is to show a clearer picture of what I did)

I did not 'adjust the size' as in adjust the bar, I just choose whatever the disk partitioned suggested:

first partition ntfs 40G
second partition fat32 this is a recovery partition
third partition is supposed to be 280G

but after resizing I discover that the ntfs partition shrinks to 11G and no more free space, why does this happen?

```

doordie@compaqnc4400:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5             271G  2.2G  255G   1% /
tmpfs                 1.5G     0  1.5G   0% /lib/init/rw
varrun                1.5G  104K  1.5G   1% /var/run
varlock               1.5G     0  1.5G   0% /var/lock
udev                  1.5G  2.8M  1.5G   1% /dev
tmpfs                 1.5G  104K  1.5G   1% /dev/shm
lrm                   1.5G  2.0M  1.5G   1% /lib/modules/2.6.27-7-generic/volatile
doordie@compaqnc4400:~$ sudo fdisk -l
[sudo] password for doordie: 

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x95aa95aa

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1226     9847813+   7  HPFS/NTFS
/dev/sda2           38209       38913     5654848+   c  W95 FAT32 (LBA)
Partition 2 does not end on cylinder boundary.
/dev/sda3            1227       38208   297057915    5  Extended
/dev/sda5            1227       37077   287973126   83  Linux
/dev/sda6           37078       38208     9084726   82  Linux swap / Solaris

Partition table entries are not in disk order

```

---

### Post by p2bc on 2009-08-11
Ok, what I would do is separate your procedures.

1) Using the LiveCD, Ubuntu / Knoppix, use GParted to resize to Windows partitions, and move the Fat32 partition. Commit those changes. Stop. reboot you system. Log into Windows, check and see everything is hunky dory. 

2) Reboot, and install Ubuntu or the remaining disk space, remember to also make a swap disk. :)

I find breaking things down into smaller step makes recovering something a little easier because it forces you veritfy as you go along. Doing everything in one shot there is no way to track where it went wrong for sure easily.

So I trying resizing your Windows partition to 40g, make sure it works, then re-install Linux

That is my advice

---

### Post by Mark Phelps on 2009-08-12
p2bc:  Excellent advice!!  

Also, if you do this in two steps, if you hose up your partitions in the first step, you have an excellent chance of recoverying them without data loss.  But if you go ahead and do the install and THEN find out your partitions are hose, you've already overwritten then, so the chances of full data recovery are very slim.

---

