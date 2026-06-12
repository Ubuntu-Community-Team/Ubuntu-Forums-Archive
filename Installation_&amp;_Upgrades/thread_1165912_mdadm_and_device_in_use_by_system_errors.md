---
title: "mdadm and device in use by system errors"
date: 2009-05-21
forum: Installation &amp; Upgrades
---

### Post by pyrodrake on 2009-05-21
After spending several hours panning through forums to no avail, I figured I'd ask the community for help on this...

We picked up 5 1.5TB hard drives that we're going for a RAID5 configuration on our server.  I had set this up before on Ubuntu 8.04 with 5 500GB HDs, and only ran into a few small problems...

I was, at first, able to successfully create a single partition on each drive, and create the RAID5 set at /dev/md0.  The devices I'm using are listed as /dev/sdb1 through /dev/sdf1.  I ran into some hardware issues shortly after that, and one of the drives was marked as 'failed.'  I have no data to loose on them yet, so I broke the RAID and was going to re-create it.  Every time I tried to re-create it, it gave me an error that "/dev/sdb1 is apparently in use by the system" and wouldn't get beyond that.  I rebooted and got the same thing.  I deleted all the partitions, rebooted, tried again, and now it gives me the following errors:

```
mdadm: Cannot open /dev/sdc1: Device or resource busy
mdadm: Cannot open /dev/sdd1: Device or resource busy
mdadm: Cannot open /dev/sde1: Device or resource busy
mdadm: Cannot open /dev/sdf1: Device or resource busy
mdadm: create aborted
```

The output of fdisk -l is as follows:

```

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29164   234259798+  83  Linux
/dev/sda2           29165       30401     9936202+   5  Extended
/dev/sda5           29165       30401     9936171   82  Linux swap / Solaris

Disk /dev/sdb: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x09f1d31c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      182401  1465136001   fd  Linux raid autodetect

Disk /dev/sdc: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0b2d65a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      182401  1465136001   fd  Linux raid autodetect

Disk /dev/sdd: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4ce7fc36

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1      182401  1465136001   fd  Linux raid autodetect

Disk /dev/sde: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9486665f

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1      182401  1465136001   fd  Linux raid autodetect

Disk /dev/sdf: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8e3b2c2d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1      182401  1465136001   fd  Linux raid autodetect

```

And the output of df -k:
```
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1            230582768   1001948 217867832   1% /
tmpfs                  1999848         0   1999848   0% /lib/init/rw
varrun                 1999848       324   1999524   1% /var/run
varlock                1999848         0   1999848   0% /var/lock
udev                   1999848       168   1999680   1% /dev
tmpfs                  1999848         0   1999848   0% /dev/shm
lrm                    1999848      2760   1997088   1% /lib/modules/2.6.28-11-server/volatile

```

And lastly, the output of mount:
```
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-11-server/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)

```

I tried [everything on this post]("http://ubuntuforums.org/showthread.php?t=872584&page=2"), but am still having a problem.  Can anyone else help???

EDIT: Also, I have the ability to delete and re-create the partitions at will, I just can't add them to the array, and I get "/dev/sdc1 is apparently in use by the system; will not make a filesystem here!" when trying mkfs.ext3 to the partition...

---

### Post by RainKap on 2009-05-21
I had a very similar problem after upgrading from Hardy to Jaunty via Intrepid... My setup is 4 x 320GB drives (sdb, sdc, sdd, sde) in RAID5. In the end I had to go through the install process from the CD (fortunately I'd backed up everything from my RAID array) to delete the partitions on the 4 drives sdb - sde, then abort the installation, then restart it to make sure the installer saw the drives as not in use, so I could repartition them, create the RAID array and format it to ext3.

Then came the next problem: the installer re-used the UUID for md0 from the old /etc/fstab instead of inserting the new UUID <grr>. The only way out of this seems to be to comment out the line in /etc/fstab, but then I can't use the RAID array!

One door opens, another closes...

Ian

---

