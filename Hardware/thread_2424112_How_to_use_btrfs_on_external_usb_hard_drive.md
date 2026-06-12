---
title: "How to use btrfs on external usb hard drive?"
date: 2019-08-03
forum: Hardware
---

### Post by lance bermudez on 2019-08-03
Need compression on the hard drive like for a freenas plex media server

the harddrive is at /dev/sdb with UUID=b70ca85a-d6ae-4d99-a073-b52af3d077a8 

on the fstab I was told to do
UUID=b70ca85a-d6ae-4d99-a073-b52af3d077a8 /home/lance/plex/zfs btrfs defaults,compress=zlib:9,autodefrag 0 0

how do I do snapshots? or fsck -y if their is corruption on the drive.

---

### Post by TheFu on 2019-08-03
I know very little about btrfs.

Compressing already compressed files, like zip, gz, and all the media files, except FLAC, is nearly useless. If you expect any additional compression, you are going to be disappointed.  When using btrfs or zfs, you have to use the specific tools for those file systems. Look for a reputable guide specific to btrfs.   Beware that btrfs lies to both du and df, so you cannot believe those tools anymore if you use btrfs.

Before you can mount a partition, you'll need to create the file system with the options you want on that partition.  This is a normal requirement, regardless of the file system used.

---

