---
title: "RAID - file system empty Help!"
date: 2008-09-03
forum: General Help
---

### Post by ehood on 2008-09-03
I'm an ubuntu noob but I came from Dos and read well enough that I setup an ubuntu desktop to run as my raid server.  It's using 3 500gb drives and has been running for almost a year.  My primary hard drive (3 partitions first one contains ubuntu) got some bad i/o errors so I used ddrescue on a live CD to copy everything to a new drive and boot from it.

I didn't touch anything related to my raid array and before all of this it was fine.

The ddrescue went well and I'm now back in ubuntu like before, except my formerly full 1TB raid array (there was about 7gig free) now says that 870.1GB out of 916.9GB is free.  It auto mounts but there are no files so I have no idea what this fantom used space is or where all my files went.

I did see during the first boot after ddrescue that it said it was rebuilding the journal but then it flashed by so I didn't see any other details.  I've since rebooted and I guess "dmesg" only shows the last boot.  I don't know enough about ubuntu logs to check somewhere else.

Things I've done:
mdadm seems to think the raid is in great shape, no problems there. gparted when /dev/md0 is selected shows /dev/md0p1 and says couldn't find valid filesystem superblock and error while trying to open /dev/md0p1 but I've read where this can be normal? (I think it always looked like this before)

I ran an fsck.ext3 -f -v, and it said there was no lost+found, I didn't have it create one because I don't want to overwrite anything. at the end it said there were still problems with the disk but it didn't list any other than the lost+found

I've got 900+ GB I can't lose, that's why it was on RAID, any help on how to figure out what the heck happened MUCH appreciated!

---

### Post by fjgaude on 2008-09-04
Okay, what does this command show:

```
sudo mdadm -D /dev/md0
```

or whatever you array is named?

---

### Post by ehood on 2008-09-08
That command results in the following (and thanks for the help):

/dev/md0:
        Version : 00.90.03
  Creation Time : Sun Apr 22 20:36:16 2007
     Raid Level : raid5
     Array Size : 976766976 (931.52 GiB 1000.21 GB)
  Used Dev Size : 488383488 (465.76 GiB 500.10 GB)
   Raid Devices : 3
  Total Devices : 3
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Mon Sep  8 17:53:16 2008
          State : clean
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 512K

           UUID : fc045029:d9fbc86f:6a0bb9b0:baad343f
         Events : 0.76

    Number   Major   Minor   RaidDevice State
       0       8        1        0      active sync   /dev/sda1
       1       8       17        1      active sync   /dev/sdb1
       2       8       33        2      active sync   /dev/sdc1

---

### Post by fjgaude on 2008-09-09
Well, seems your raid is in good shape... have you tried to mount the array?

Gparted doesn't understand raid, so it shows things that have no meaning.

What does your /etc/fstab file look like?

---

### Post by ehood on 2008-09-09
It mounts fine, it's just empty which is a MAJOR problem because all but 7gigs of it was full of my files. :)

Here is /etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=49a50de5-7cf4-44d5-ac18-57eed40097f5 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda2
UUID=ab05f3c5-7efe-4f75-95f5-5ffb9888b5ff none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/md0	/media/raid	auto	defaults	0	3

---

### Post by fjgaude on 2008-09-10
In your fstab file:

```
/dev/md0 /media/raid auto defaults 0 3
```

It should be:

```
/dev/md0 /media/raid auto defaults 0 0
```

or 

```
/dev/md0 /media/raid auto defaults 0 2
```

I can't say if the "3" would do any harm. Read the man fstab pages to see with the number mean, do.

I don't have any suggestions on why the data is not showing up.

---

