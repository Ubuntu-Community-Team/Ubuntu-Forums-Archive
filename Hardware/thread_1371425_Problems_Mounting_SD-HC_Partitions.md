---
title: "Problems Mounting SD-HC Partitions"
date: 2010-01-03
forum: Hardware
---

### Post by JohnnySage50307 on 2010-01-03
I recently acquired a BeagleBoard system for a robot I'm working on, and I'm attempting to install Jaunty onto it.  Here are a few websites I've referenced:

[http://elinux.org/BeagleBoardUbuntu#Recommended_Beagle_Software](http://elinux.org/BeagleBoardUbuntu#Recommended_Beagle_Software)
[http://code.google.com/p/beagleboard/wiki/LinuxBootDiskFormat](http://code.google.com/p/beagleboard/wiki/LinuxBootDiskFormat)
[http://elinux.org/BeagleBoardBeginners#SD_card_setup](http://elinux.org/BeagleBoardBeginners#SD_card_setup)

The third one assumes a mounting of an SD card in the /mnt directory.  None of the instructions from the previous two attempt to re-mount the partitions, yet to decompress the tarball you have to be in the directory of those partitions.

After using fdisk, I have the following unmounted partitions: /dev/mmcblk0p1 and /dev/mmcblk0p2 respectively.  I used
```
sudo mount -v /dev/mmcblk0p1 /mnt
sudo mount -v /dev/mmcblk0p2 /mount
```
both appear to be functioning properly, yet no new filesystems are available in the /mnt directory (cd also claims that the directories don't exist).  Oddly enough, if you attempt to umount /mnt/mmcblk0p1 or /mnt/mmcblk0p2, it claims that they are not mounted to begin with (according to mtab).

Can someone please help me and explain how to finish this?  I have already completed the rootstock and have the tarball required to build the root filesystem, and all I have left to do is load it and load on the boot images.

---

