---
title: "External NTFS drive Can't read superblock"
date: 2012-12-02
forum: Hardware
---

### Post by madmikeismad on 2012-12-02
Looked all over and can't find a lot of ntfs answers for this.

Drive is a western digital with 2 partitions, but its only showing up as 1 device, even in /dev

Try to mount it out of curiosity and get this:

> root@madmike-laptop:/home/madmike# mount /dev/sdb test/
mount: /dev/sdb: can't read superblock

> root@madmike-laptop:/home/madmike# lsusb
Bus 001 Device 003: ID 1058:1100 Western Digital Technologies, Inc. 
Bus 002 Device 003: ID 1307:1171 Transcend Information, Inc. Fingerprint Reader
Bus 002 Device 004: ID 04f2:b109 Chicony Electronics Co., Ltd 
Bus 003 Device 002: ID 0a5c:2151 Broadcom Corp. Bluetooth
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

> root@madmike-laptop:/home/madmike# ls /dev/sd
sda   sda1  sda2  sda5  sdb

Tried regular fsck on it, and got this.

> root@madmike-laptop:/home/madmike# fsck /dev/sdb 
fsck from util-linux 2.20.1
e2fsck 1.42.5 (29-Jul-2012)
fsck.ext2: Attempt to read block from filesystem resulted in short read while trying to open /dev/sdb
Could this be a zero-length partition?

> root@madmike-laptop:/home/madmike# ntfsck /dev/sdb
Failed to read boot sector.

Also tried this just in case after googling it:

> root@madmike-laptop:/home/madmike# dumpe2fs /dev/sdb | grep superblock
dumpe2fs 1.42.5 (29-Jul-2012)
dumpe2fs: Attempt to read block from filesystem resulted in short read while trying to open /dev/sdb
Couldn't find valid filesystem superblock.

So now I'm at a loss.  On a windows box it is recognized, but windows just searches for driver and won't ever actually mount it.  I've never had to mess with or fix hardware before.  Any suggestions?

EDIT:  I should add it was working just fine till today.

---

### Post by madmikeismad on 2012-12-04
Bump.

---

### Post by ahallubuntu on 2012-12-04
/dev/sdb references the drive, not the partitions.  You have to mount individual partitions, like this:

```
mount /dev/sdb1 /mnt
```

Yes, I know sdb1 isn't showing up for you.  Perhaps you  meant to run fdisk on it not "fsck?"  Try this:

```
sudo fdisk -l /dev/sdb
```

What's the history of this drive?  It's possible the partition table got corrupted...drive could be failing, etc.

Can you plug in into another computer (a Windows computer) just for fun?  Any difference?

---

### Post by oldfred on 2012-12-05
You cannot run fsck on NTFS formatted partitions. fsck is for the ext Linux family of formats. You have to run chkdsk from Windows.

       chkdsk c: /r
    
c: is normally the Windows system partition change to d: or whatever Windows mounts the external as.

---

### Post by madmikeismad on 2012-12-05
> **ahallubuntu said:**
> /dev/sdb references the drive, not the partitions.  You have to mount individual partitions, like this:

```
mount /dev/sdb1 /mnt
```

Yes, I know sdb1 isn't showing up for you.  Perhaps you  meant to run fdisk on it not "fsck?"  Try this:

```
sudo fdisk -l /dev/sdb
```

What's the history of this drive?  It's possible the partition table got corrupted...drive could be failing, etc.

Can you plug in into another computer (a Windows computer) just for fun?  Any difference?

fdisk shows absolutely nothing.  If I plug into a windows box, windows shows the little icon in the systray saying it's searching for driver, and it just does it forever until I unplug the drive.

Drive was working fine until this happened.  Also, now when I plug it in, disk managers see it as a 2.2Tb drive, even though it's only 1Tb.  And I can't do anything but format it.  I'm trying to hold off on that until i'm sure I can't recover the data.


> **oldfred said:**
> You cannot run fsck on NTFS formatted partitions. fsck is for the ext Linux family of formats. You have to run chkdsk from Windows.

       chkdsk c: /r
    
c: is normally the Windows system partition change to d: or whatever Windows mounts the external as.

I ran the fsck just for fun, hoping it might give an error I can use, and the ntfsck, and neither worked.

I'd run chkdsk, but I can't even get it to mount.  I'll keep trying though.   
EDIT:  Even though it doesn't mount, I tried "chkdsk e: /r" (r was the next letter available, so I assumed), and it says "cannot open volume for direct access"

Thanks for the replies.

---

