---
title: "XFS harddrives/partitions suddenly unable to mount"
date: 2013-06-20
forum: Hardware
---

### Post by Svip on 2013-06-20
I have a set up of several partitions.

One on / and one on /home.  In addition, I have a Windows-partition, as well as three additional XFS partitions for storage of large files (such as films and television programmes).

However, now neither /dev/sdb2 and /dev/sdc1 will mount (both XFS); /dev/sdb1 (also XFS) mounts without complaint.  However, despite being mounted without complaint, it does throw input/output errors when I ls anything on it (so it is sort of not really mounted).

When I attempt to mount them, I get the following response:
```
mount: /dev/sdc1: can't read superblock
```
(Same for /dev/sdb2.)

So I do an xfs_check on them.
```
xfs_check: /dev/sdc1 is invalid (cannot read first 512 bytes)
```

Hmm, that certainly seems to coincide with the idea that the superblock cannot be read.  So I try running hdparm -N on them:

```
/dev/sdc:
 HDIO_DRIVE_CMD(identify) failed: Input/output error
/dev/sdc1:
 HDIO_DRIVE_CMD(identify) failed: Input/output error

```

Having read [this thread](http://oss.sgi.com/archives/xfs/2012-01/msg00349.html), the issue seems to be about reporting the wrong size of the disk.  [This thread (linked in the other) suggest a similar issue](https://www.linuxquestions.org/questions/linux-general-1/cannot-mount-hard-disk-block-count-exceeds-size-of-device-bad-partition-table-880149/), with the wrong reporting of file size, as well as the suggestion of simply resizing the partitions (to the same size) to solve the issue by correcting the size reporting.  However, resizing is not possible for XFS.

Just FYI:

```
# fdisk -s /dev/sdb
976762584
# fdisk -s /dev/sdb1
511999551
# fdisk -s /dev/sdb2
464760450
# fdisk -s /dev/sdc
976762584
# fdisk -s /dev/sdc1
976760001
```

Any suggestions on how proceed?  And is it possible I will be able to mount them again?

---

### Post by TheFu on 2013-06-20
I'd start with the simple things first.
* Use UUID-based mounts, not device-based mounts.  This will mean that swapping ports doesn't matter.  Machines with lots of HDDs connected have had issues with race conditions changing the device name during boot. UUIDs handle that issue.
* swap the sata ports used. Reseating might be enough. Do both sides of the connection.
* swap the cables.  Bad SATA cables definitely exist. They also fail over time.
* use disk checking programs to validate that your HDD controller is working 100% correctly.  I can't think of the name now, sorry. Google will recommend.

And of course, have 3-2-1 backups for everything. Your data is clearly at risk, so if you don't already have backup religion, now is the time to get it. 

If you are using AF HDDs, it has been recommended to stop using fdisk and fdisk-like tools. Use parted or gparted going forward to support GPT and MBR as well as to automatically align partitions for the best performance. fdisk doesn't do those things - at least the last time I checked.

The data from the boot-info script [https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) would probably be helpful here too. It will ensure that we work with facts about your HDD and partitions.

---

### Post by SeijiSensei on 2013-06-20
I've found XFS to be horribly fragile especially when subjected to power outages.  If you manage to retrieve your files, I suggest using ext4 everywhere.  While XFS was designed to handle large files, modern filesystems like ext4 do just as well.

I had a lot of video files on an XFS-formatted external drive.  After a couple of bouts where some of the files were lost after a power outage, I switched everything to ext4.  It works fine.

---

### Post by Svip on 2013-06-21
u> **TheFu said:**
> I'd start with the simple things first.
* Use UUID-based mounts, not device-based mounts.  This will mean that swapping ports doesn't matter.  Machines with lots of HDDs connected have had issues with race conditions changing the device name during boot. UUIDs handle that issue.

In my /etc/fstab they do appear by UUID.

> **TheFu said:**
> * swap the sata ports used. Reseating might be enough. Do both sides of the connection.

That's not a bad idea.

> **TheFu said:**
> * swap the cables.  Bad SATA cables definitely exist. They also fail over time.

I find it unlikely that two SATA cables failed at the same time (while the computer was on, by the way).

> **TheFu said:**
> * use disk checking programs to validate that your HDD controller is working 100% correctly.  I can't think of the name now, sorry. Google will recommend.

Since these are Samsung disks, I imagine their HUTIL or are you thinking of the Ultimate Boot Disc?

> **TheFu said:**
> And of course, have 3-2-1 backups for everything. Your data is clearly at risk, so if you don't already have backup religion, now is the time to get it. 

If you are using AF HDDs, it has been recommended to stop using fdisk and fdisk-like tools. Use parted or gparted going forward to support GPT and MBR as well as to automatically align partitions for the best performance. fdisk doesn't do those things - at least the last time I checked.

I only used fdisk to showcase the block size of each partition.  GParted won't even recognise the devices exists.

> **TheFu said:**
> The data from the boot-info script [https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) would probably be helpful here too. It will ensure that we work with facts about your HDD and partitions.

[http://paste.ubuntu.com/5785935/](http://paste.ubuntu.com/5785935/)

> **SeijiSensei said:**
> I've found XFS to be horribly fragile especially when subjected to power outages.  If you manage to retrieve your files, I suggest using ext4 everywhere.  While XFS was designed to handle large files, modern filesystems like ext4 do just as well.

I had a lot of video files on an XFS-formatted external drive.  After a couple of bouts where some of the files were lost after a power outage, I switched everything to ext4.  It works fine.

I am still not convinced this is an issue with XFS, but I could be wrong.  I have just been on holiday and when I returned, they worked fine.  Suddenly - during while my computer was turned on - they stopped working.  Why would they fail during the same uptime where they have worked fine?

Anyway, I will try moving around the cables.

Oh and, thank you for your replies.

**Update:** Apparently, exchanging the SATA cables made it work.  Thank you.

---

