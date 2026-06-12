---
title: "fixing filesystem panic errors on locked usb drive"
date: 2008-07-12
forum: Hardware
---

### Post by souldances on 2008-07-12
I have a 500gb external usb hard drive (wd 'my book') all one partition using fat32 that has started mounting as locked read-only.  It auto-mounts, so it doesn't show in fstab.  It showed a buttload of filesystem panic errors listed when I ran ...that command I don't remember.  (I'm not sure if it was an imperial buttload or a troy buttload, either :-P)  When I tried unmounting and running dosfsck, it gave a bunch of 'not auto correcting this' lines then started displaying a bunch of binary gobbledy-gook, so I acted like a panicy n00b and closed terminal.  It appears to have survived that with no ill effects.

Here's what 'fdisk -l' says about the disk:
Disk /dev/sda: 500.1 GB, 500107862016 bytes

255 heads, 63 sectors/track, 60801 cylinders

Units = cylinders of 16065 * 512 = 8225280 bytes

Disk identifier: 0x44fdfe06



   Device Boot      Start         End      Blocks   Id  System

/dev/sda1               1       60801   488384001    c  W95 FAT32 (LBA)

fsck gives this:
fsck 1.40.2 (12-Jul-2007)

dosfsck 2.11, 12 Mar 2005, FAT32, LFN

There are differences between boot sector and its backup.

Differences: (offset:original/backup)

  67:ef/54, 68:1d/1f, 69:a0/fb, 70:5d/16

1) Copy original to backup

2) Copy backup to original

3) No action

? 

(I chose 3 – no action)

Since the drive is locked apparently due to the filesystem panics, am I better off using the copy backup to original option in fsck, or are there other/better ways to fix it?  Is there the potential to lose any data doing this?  Is there a way to undo this if it's not where the problem lies?  I don't want to risk playing 'what's this do?' when the obviously wiser choice is to get some guidance from those in the know...

---

