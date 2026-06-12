---
title: "Can't mount ext3 partition on microSD card"
date: 2010-02-18
forum: Hardware
---

### Post by joedoc on 2010-02-18
Hi, everyone;

This is really a Mint question, but since the distro is based on Ubuntu (and I didn't get any responses on the Mint forums), I thought I'd drop this here to see if I get a response.

I'm running Mint 8 KDE CE on my HP laptop. All works well, except for one annoyance I can't seem to figure out.

I have a T-Mobile G1 Android phone that is rooted and modded. Part of the mod was creating an ext3 partition on the 8GB microSD card for use by the phone to store apps. I have always been able to mount this microSD card on the laptop (either in the SD slot or directly from the phone) and have complete access to the two partitions on it (the other is a vfat partition for storing media and stuff).

On this version of Mint, when I mount the card, the vfat partition is available when mounted (I can see and at least read everything). But when the ext3 partitions is mounted, I get a message from Dolphin (and other tools) "could not enter folder /media/disk-1". The partition is shown as mounted on the desktop (I have to unmount it before I remove the card or the phone). But I can't see anything on the partition. I need to access this so i can back up the apps folders to an external drive.

Here's the rub: when I'm logged in using the original setup account (the initial account I created when I installed Mint 8 ), I can mount the partition. However, as the regular user account that I normally use (and that I created after installing Mint 8 ), the partition won't mount. On Mint 7, I also didn't have this problem because I had only a single user account.

I checked my account's group memberships and all seems correct. I've searched through config files and the like, and can't seem to find anything relating to this issue.

The card is mounted now, and here are the related results from ~mount~:

/dev/mmcblk0p1 on /media/disk type vfat (rw,nosuid,nodev,uhelper=hal,uid=1001,utf8,shortname=mixed,flush)
/dev/mmcblk0p2 on /media/disk-1 type ext3 (rw,nosuid,nodev,uhelper=hal)

The second partition (...0p2) is the one in question. The uid in the vfat partition line is the user id of this account.

Having the ability to read and write to this partition would be helpful in case I need to do a file system repair or a simple backup or restore.

If anyone has any advice on this, it would be greatly appreciated.

---

