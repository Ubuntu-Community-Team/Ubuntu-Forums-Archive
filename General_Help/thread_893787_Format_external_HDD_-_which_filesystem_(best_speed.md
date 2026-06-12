---
title: "Format external HDD - which filesystem? (best speed &amp; size)"
date: 2008-08-18
forum: General Help
---

### Post by shusai on 2008-08-18
Sorry for asking this question, I know there are some similar threads, but I could not find anything about the speed of the different filesystems yet.

Today I bought a Western Digital Elements 1000GB external hard disk and have been playing around a few hours now, trying to find out how I should format it.
I want to use it to backup mostly large files (1-2GB), so I am looking for the best performance in continuous writing.

I already tried FAT32, NTFS and ext3 and always copied 15 files with about 12GB to the HDD. 
Here are the differences;

_1. FAT32:_
GParted: Size 931.51GB Used 0 Unused 931.51GB
17 min to copy all files, speed from 23MB/sec at the beginning to 11.9MB/sec at the end 

_2. NTFS:_
GParted: Size 931.51GB Used 93.59MB Unused 931.42GB (Nautilus: Free Space: 931.4 GB)
25 min to copy all files, speed from 15MB/sec at the beginning to 7.9MB/sec at the end 

_3. ext3:_
GParted: Size 931.51 GB, Used 7.53, Unused 923.98GB (Nautilus: Free Space: 877.4 GB)
15 min to copy all files, speed from 26MB/sec at the beginning to 13.1MB/sec at the end

ext3 seems to be the fastest filesystem, but it takes away 60 GB, what for?


What do you think should I use?

---

### Post by mb_webguy on 2008-08-18
There are a few other things than speed that you need to consider if this is going to be a backup drive for large files.

FAT32 has a file size limit of 4GB.  If the files you're dealing with may approach this size, you definitely don't want to use FAT32.

Also, for a backup drive you probably want a journaling file system so you're less likely to lose data in case of power loss or system crash.  FAT32 isn't a journaling file system, and I don't believe the Linux ntfs-3g driver supports journaling.

Therefore, if you're using this drive to backup files on a Linux system, I'd without a doubt go with ext3.  It's the fastest, it has a sufficiently large (in the terabyte range, I believe) file size limit, and it is a journaling file system.  As an added bonus, using ext3 will let you use Linux file permissions on the drive, which ntfs doesn't support.

If you're planning on sharing this drive between Linux and Windows systems, you'll probably run in to the same problem with journaling on ext3 on Windows as you have with ntfs on Linux, since I don't believe the third-party Windows ext3 driver supports journaling, either.  But since ext3 is still the faster file system, it's still the better choice.

As for the missing space...  Hard drive manufacturers don't use the same measure for GB as the rest of the computing world.  The standard Gigabyte is 1024^3 bytes, which is 1024MB.  Hard drive manufacturers, however, use 1000^3 bytes for 1GB, which means that the actual storage space of a hard drive is about 93% of its given size (which, if you do the math, is the exact amount GParted is giving you for the size).  As for the different size listed in Nautilus, ignore that.  Nautilus isn't very good at accurately reporting drive space, for some reason.

---

### Post by shusai on 2008-08-21
Meanwhile I tried some more filesystems:

_ext2:_
GParted: Size 931.51 Used 7.41GB Unused 924.10 (Nautilus: Free Space: 877.4 GB (5% reserverved for root) /924.1GB)
15 min to copy all files, speed from 24MB/sec at the beginning to 13MB/sec at the end

_ReiserFS:_
GParted: Size 931.51 Used 61.19MB Unused 931.51 (Nautilus: Free Space: 931.5GB)
16 min to copy all files, speed from 20MB/sec at the beginning to 13.3MB/sec at the end

_XFS:_
GParted: Size 931.51 Used 128.58MB Unused 931.140 (Nautilus: Free Space: 931.4GB)
15 min to copy all files, speed from 25MB/sec at the beginning to 13.5MB/sec at the end


So it looks like FAT32 and NTFS are a little bit slow, all other filesystems seem to be almost identically fast, a small difference can be found in the actually useable disk space. 

I also did find out why there are missing almost 60GB when using ext2 or ext3, there are 5% of the whole disk reserved for root (see also [here]("http://ubuntuforums.org/showthread.php?t=215177")). 
This can be disabled using the following command to the unmounted disk (/dev/sdb1 in my case):

```
sudo tune2fs -m 0 /dev/sdb1
```

There are still about 7GB used I could not find out why, but that shouldn't be a big problem with todays hard disks.

I now use the disk formatted to XFS which seems to work pretty good in daily use, writing to it almost never drops under 20MB/sec, reading from it is around 30MB/sec, which I think is not so bad for an USB-drive.

---

