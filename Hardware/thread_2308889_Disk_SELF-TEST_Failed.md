---
title: "Disk SELF-TEST Failed"
date: 2016-01-06
forum: Hardware
---

### Post by t4ggs on 2016-01-06
Hi tested a disk and got this error, I'm panicking since I don't really understand what's the error or how to solve it.

Any idea?

Thanks!!

See attached picture.
[ATTACH=CONFIG]266572[/ATTACH]

---

### Post by weatherman2 on 2016-01-06
You have one pending sector - one sector that cannot be read.  That could be causing the self-test to fail.

I prefer GSmartControl for accessing S.M.A.R.T. data and running tests.  I would probably boot a live USB of Ubuntu - or some other Linux disc - and install/run GSmartControl from there, to avoid using that disk for now.

Also, you need to make sure all of your data from that disk is backed up! Hard drives routinely fail and if they do, you could lose some/all of your data.  Don't wait to make a backup.

If you have one pending sector, it may be possible to write to it and clear it.  Sometimes that works, sometimes it doesn't - and if it doesn't, you may need to replace the hard disk.

---

### Post by t4ggs on 2016-02-01
I created a file with the bad blocks I have.

The file looks like this:
900588120
900588121
900588122
900588123

Now, I tried running this command in order to prevent those sectors from being used 

sudo fsck.ext4 -l bad-blocks /dev/sdb

But I get the following:

ytagger@tagger-server:~$ sudo fsck.ext4 -l bad-blocks /dev/sdb
e2fsck 1.42.12 (29-Aug-2014)
ext2fs_open2: Bad magic number in super-block
fsck.ext4: Superblock invalid, trying backup blocks...
fsck.ext4: Bad magic number in super-block while trying to open /dev/sdb

The superblock could not be read or does not describe a valid ext2/ext3/ext4
filesystem.  If the device is valid and it really contains an ext2/ext3/ext4
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
 or
    e2fsck -b 32768 <device>


This:
sudo e2fsck -b 32768 /dev/sdb
and this:
sudo e2fsck -b 8193 /dev/sdb
Doesn't help.


Could somebody please explain what am I doing wrong?

---

### Post by matt_symes on 2016-02-01
Hi
> 
ytagger@tagger-server:~$ sudo fsck.ext4 -l bad-blocks /dev/sdb
e2fsck 1.42.12 (29-Aug-2014)
ext2fs_open2: Bad magic number in super-block
fsck.ext4: Superblock invalid, trying backup blocks...
fsck.ext4: Bad magic number in super-block while trying to open /dev/sdb

You run fsck on a filingsystem that resides in a partition, not on the drive itself.

You wnt to be running something like

```
sudo fsck.ext4 -l bad-blocks /dev/sdb**1**
```

Where sdb**1** may be your partition. You'll want to adjust sda1 to the device that represents the partition you want to run fsck on.

Kind regards

---

### Post by t4ggs on 2016-02-01
Thanks, I thought I should do it for the disk and not the partition.

How do I verify that those blocks are indeed blocked? Should I check for bad blocks again?

---

### Post by matt_symes on 2016-02-01
Hi

> **t4ggs said:**
> Thanks, I thought I should do it for the disk and not the partition.

How do I verify that those blocks are indeed blocked? Should I check for bad blocks again?

You can get the list of bad block the ext4 stores using the *dumpe2fs* command.

```
sudo dumpe2fs -b /dev/sdaX
```

Where X is the partition number.

From 

```
man 8 dumpe2fs
```

> -b     print the blocks which are reserved as bad in the filesystem.

Anyway, I've just taken a better look at the image you posted in post #1.

It looks like you have an 'uncorrectable sector count' and a 'current pending sector count' of 1. You also have 3 sectors that contain 'uncorrectable errors'.

I suspect the reason why the SMART test failed is due to the 'uncorrectable errors'.

You want to be backing up any important data from that drive on a regular basic. This is alway good practice anyway, but this is especially the case with that drive.

I would have (may have depending on the situation) run fsck differently than the way you did.

I would have booted into a LiveUSB (or other live environment) and run fsck.ext4 using either the -c or -cc option; something along the lines of

```
sudo fsck.ext4 -cc /dev/sdYX
```

Where YX are the drive (Y) and the partition on that drive (X).

To understand the difference between *-c* and *-cc*....
```

       -c     This  option causes e2fsck to use badblocks(8) program to do a read-only scan of the device in order to find
              any bad blocks.  If any bad blocks are found, they are added to the bad block inode  to  prevent  them  from
              being  allocated to a file or directory.  If this option is specified twice, then the bad block scan will be
              done using a non-destructive read-write test.
```

I hope that kind of helps.

Feel free to ask any more questions.

Please remember to mark this thread as SOLVED using the thread tools menu above post #1 if, at some point, you are happy this thread has answered your questions. It'll help others looking for a similar solution and is an easy way to give back to the community.

Kind regards

---

