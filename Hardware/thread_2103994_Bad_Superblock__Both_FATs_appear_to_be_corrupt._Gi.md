---
title: "Bad Superblock / Both FATs appear to be corrupt. Giving up."
date: 2013-01-11
forum: Hardware
---

### Post by gnice3d on 2013-01-11
For the second time in a year, I had a windows system crash with a large capacity (500GB) FAT32 partitioned drive mounted and amidst the crash, it somehow obliterated both the primary and backup boot sectors making the drive unmountable and unrecoverable with standard fsck tools.

The first time this happened, I researched through hundreds of threads and could not find a way to rebuild the partition map and I resigned to proceeding with raw data recovery which took several days (USB to USB).

With the info I had gathered last time and a ****-ton of trial and error today, I was abe to come up with a routine to rebuild the partition map while keeping all of data in tact.

sudo apt-get install testdisk
sudo testdisk

>Create a new log file
[Choose Disk]
>Intel/PC partition
>Advanced
[Choose Partition]
>Boot
>Repair FAT
[Accept Defaults and Write]
>(Q)uit until exited

Give Microsoft the bird and disco/reconnect drive.

---

### Post by ahallubuntu on 2013-01-11
While I encourage you to dump Windows for the wonderful world of Linux, it doesn't sound like Windows caused your hard drive issues.  Like it or not, hard drives have moving parts and are one of the least reliable pieces of a computer (that and a power supply).  I've replaced many failing or failed hard drives over the years.  It has little to do with the operating system.  Even Mac hard drives fail.

My philosophy is to check hard drive health with S.M.A.R.T and make regular backups.  I EXPECT my hard drives to fail.  I buy duplicates of my archive drives; if I buy a 2TB drive, I buy two identical drives, one a shadow of the other. (You can RAID but I don't - RAID protects you only against hard drive failure, not file system corruption, accidental deletion, etc.).  Learn how to make regular, reliable backups even of your OS.  Learn how to restore a backup quickly - try it before you actually need to.  (A spare drive is really  handy for that.)  Then when a drive actually does fail, it's an annoyance not a catastrophe.

---

### Post by ahallubuntu on 2013-01-11
By the way: if you do use Windows, I encourage you to use NTFS not FAT32.  NTFS is much more robust - it has journaling built in (FAT32 doesn't), so it can recover from problems better than FAT32 can.

---

### Post by skaunov on 2013-08-31
> >Boot
>**Repair** FAT
[Accept Defaults and Write]

I had a question.

``Please specify what kind of job is it? I have to candidate options there: *Ba**ck-up, *and *Rebuild.* The first one copy back-up copy of boot sector and I didn't get what exactly do the other one. :(

But found this: "http://www.cgsecurity.org/wiki/Advanced_FAT_Repair#Rebuild_a_valid_FAT_boot_sector" useful. :)

---

