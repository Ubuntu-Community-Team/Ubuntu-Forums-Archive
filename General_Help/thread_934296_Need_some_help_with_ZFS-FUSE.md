---
title: "Need some help with ZFS-FUSE"
date: 2008-09-30
forum: General Help
---

### Post by kochakaden on 2008-09-30
I've recently reinstalled my file server and decided to go with ZFS instead of LVM+Raid this time around.

I must say that ZFS is much much much much simpler to implement, but I have a few questions for anyone else who is running this in a real environment and might know:


**1.** How do I get ZFS to start up along with the machine?  Is there an init.d script for this somewhere?


**2.** I created my zfs pool like so:
```
# zpool create -f tank raidz2 /dev/sdb /dev/sdc /dev/sdd /dev/sde /dev/sdf /dev/sdg /dev/sdh
# zpool status
  pool: tank
 state: ONLINE
 scrub: none requested
config:

        NAME        STATE     READ WRITE CKSUM
        tank        ONLINE       0     0     0
          raidz2    ONLINE       0     0     0
            sdb     ONLINE       0     0     0
            sdc     ONLINE       0     0     0
            sdd     ONLINE       0     0     0
            sde     ONLINE       0     0     0
            sdf     ONLINE       0     0     0
            sdg     ONLINE       0     0     0
            sdh     ONLINE       0     0     0

errors: No known data errors
# zpool list
NAME   SIZE   USED  AVAIL    CAP  HEALTH  ALTROOT
tank  2.03T   189K  2.03T     0%  ONLINE  -
# zfs create tank/data
# df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1             48444392   2553204  43449712   6% /
varrun                 1031660       100   1031560   1% /var/run
varlock                1031660         0   1031660   0% /var/lock
udev                   1031660        84   1031576   1% /dev
devshm                 1031660        48   1031612   1% /dev/shm
lrm                    1031660     43744    987916   5% /lib/modules/2.6.24-19-generic/volatile
tank                 1526353776        39 1526353738   1% /tank
tank/data            1526353776        39 1526353738   1% /tank/data

```
zpool shows tank as having 2.03TB available, but df only shows 1.5TB.  Is this because 500 gigs are being used for parity?


**3.** I haven't been able to find a solid answer on this:  In my current array, I have the following sized drives: 3x500gig, 2x750gig, 2x320gig.  Is the raidz2 array limited to 320 gigs per drive?  If I swap out one of the 320 gig drives and put a 1TB drive in its place, will that increase my storage, or will the extra capacity sit unused?

---

### Post by parameter on 2009-01-03
> **kochakaden said:**
> 
zpool shows tank as having 2.03TB available, but df only shows 1.5TB.  Is this because 500 gigs are being used for parity?

Yes. raidz2 can survive two drive failures so you lose two drives worth of space for parity information.

> I haven't been able to find a solid answer on this:  In my current array, I have the following sized drives: 3x500gig, 2x750gig, 2x320gig.  Is the raidz2 array limited to 320 gigs per drive?
With raidz or raidz2 all drives must have the same stripe size. Therefore the space used on each drive is as big as the smallest drive or partition. Bottom line, you are only using 320GB for raidz2 on all of your drives. The rest of the space on your 500GB and 750GB drives are not being used.

> If I swap out one of the 320 gig drives and put a 1TB drive in its place, will that increase my storage, or will the extra capacity sit unused?

The extra capacity will sit unused.

Also, it is recommended on the zfs-fuse mailing list not to use zfs-fuse on the whole disk device (like sda) but instead to use on partitions (like sda1) even if you create one partition that uses the entire disk.  It may work by addressing the whole disk but people have run into complications if there is repair or recovery that needs to be done later.

---

### Post by loonyjuice on 2010-02-23
Hi, just to follow on I have some further questions and I'm wondering how you are getting on?

I've been reading this: [http://www.solarisinternals.com/wiki/index.php/ZFS_Best_Practices_Guide](http://www.solarisinternals.com/wiki/index.php/ZFS_Best_Practices_Guide)

which recommends using whole disks, not partitions!

I've setup a zfs stripe on a virtualbox ubuntu 10.04 installation, and it seems to use all the space accross 3x 2GB and 2x 4GB disks. It reports the available space as 14GB at least, which is great!

I can also report that it auto-mounts the partitions on boot. However, and this is where my questions come in:

1. It auto-mounts, but it isn't mounted ready by the time the system is up. There seems to be a delay for the partition to be available of about five minutes after logging in (via ssh) before the partition is available! During this time top reports a 100% cpu usage for disk activity (the wa%) Is this normal? Can it be chaged to wait? If I have my home area on the zfs pool then I fail to see how this will work...

EDIT:
I just rebooted again and waited to see how long it takes, whilst waiting after a few minutes I did this all at once:

root@Sandbox:/zfs$ ls
root@Sandbox:/zfs$ cd san
root@Sandbox:/zfs/san$ ls
projects
root@Sandbox:/zfs/san$

So, what I'm seeing here is a directory that is empty until I cd to a known subdirectory, which then makes itself known!

2. I tried using the sharesmb=on, but it doesn't show up as being available on a windows share. Can anyone confirm this works or have I missed something?

Aside from that, this seems like a great filesystem, until btrfs comes along. I'm just apprehensive to use it fulltime on my server instead of ext3.

Any thoughts?

M.

---

