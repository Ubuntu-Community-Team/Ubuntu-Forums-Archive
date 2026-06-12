---
title: "Retrieve data from NAS mirrored drive..."
date: 2010-01-08
forum: Hardware
---

### Post by MonsterDuc on 2010-01-08
Hi,
I had a Buffalo Linkstation Pro Duo with two 500 GB HDs.  The drives were mirrored. The unit recently broke and I am trying to retrieve the data from one of the drives so I removed it and connected it to my desktop.

I can see the drive (sda info removed):
```
sudo fdisk -l
Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd7cb4bad

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         125     1004031   83  Linux
/dev/sdb2             126         748     5004247+  83  Linux
/dev/sdb4             749       60801   482375722+   5  Extended
/dev/sdb5             749         873     1004031   82  Linux swap / Solaris
/dev/sdb6             874       60690   480480021   83  Linux

```

I believe the NAS used XFS (or XFS 4 if there is such a thing) filesystem.

I tried mounting but no luck:
```
sudo mount -t xfs /dev/sdb6 /mnt/hd
mount: /dev/sdb6: can't read superblock
```

No luck with standard ext/ext2/ext3 either:
```
sudo mount -t ext3 /dev/sdb6 /mnt/hd
mount: wrong fs type, bad option, bad superblock on /dev/sdb6,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

dmesg from the xfs mount attempt:
```
[14766.499500] I/O error in filesystem ("sdb6") meta-data dev sdb6 block 0x728e2af8       ("xfs_read_buf") error 5 buf count 4096
[14766.499509] XFS: size check 2 failed
[14828.584671] VFS: Can't find ext3 filesystem on dev sdb6.
[14883.992197] attempt to access beyond end of device
[14883.992208] sdb6: rw=0, want=1921919744, limit=960960042
[14883.992222] I/O error in filesystem ("sdb6") meta-data dev sdb6 block 0x728e2af8       ("xfs_read_buf") error 5 buf count 4096
[14883.992233] XFS: size check 2 failed

```

Using gparted the sdb6 partition gets a warning triangle...

Any thoughts or suggestions?? 

Thank you!

---

### Post by MonsterDuc on 2010-01-09
I was able to retrieve files off the drive using PhotoRec. Problem is it does not restore the directory structure, plus it renames all files so some generic string.

But at least I know the data is intact.

Still looking for some advise on how to access the hard disk as a filesystem...any thoughts appreciated!

THanks!

---

### Post by MonsterDuc on 2010-01-09
bumpey

---

### Post by MonsterDuc on 2010-01-11
Not many replies but I'll update anyways in case someone else runs into this. 

Data could be retrieved with programs like PhotoRec, Foremost and Scalpel, but the directory structure and filenames were not intact. Almost pointless if you have thousands upon thousands of files.

The partition on the drive with the data was an XFS device. Attempting to mount didn't work (see above for error message).  I installed xfsprogs (apt-get install xfsprogs) then ran xfs_repair on sdb6. xfs_repair found the bad superblock and repaired it.  I was then successful in mounting the device, and could then access the data.

I will not be buying another NAS from Buffalo for sure! 

Cheers and Happy New Year!

---

### Post by MonsterDuc on 2010-02-04
Replying to my own thread again (what could be more fun!).

Just need to set the record straight with Buffalo.  Support came out strong and accepted the malfunctioning NAS, even though I had opened the box up (to restore my data).  They shipped me a new replacement that arrived today.  So kudos to Buffalotech, and grumpy me stands corrected.

---

### Post by kjano on 2010-03-05
thanks for your postings and especially for posting the solution!

after using xfs_repair i get:

ERROR: The filesystem has valuable metadata changes in a log which needs to
be replayed.  Mount the filesystem to replay the log, and unmount it before
re-running xfs_repair.  If you are unable to mount the filesystem, then use
the -L option to destroy the log and attempt a repair.
Note that destroying the log may cause corruption -- please attempt a mount
of the filesystem before doing this.

xyz:~$ sudo mount -t xfs /dev/sdb6 /media/external 
mount: Structure needs cleaning

Hence i had to use the -L option :-(. Now i can mount sb6 but the only folder I see is the lost and found folder with many GB of data with random names and folders. finding, selecting, and restructuring my data this way would take some hundred years....update: actually, most of the relevant files are in some single folders, i hope that i will be able to recover like 90% of my data, the other folders only contain several files per folder (of course these files may still be very relevant)... 

any ideas?

by the way, mounting sdb1 using ext3 also only shows the lost and found folder (which is empty)...?

---

