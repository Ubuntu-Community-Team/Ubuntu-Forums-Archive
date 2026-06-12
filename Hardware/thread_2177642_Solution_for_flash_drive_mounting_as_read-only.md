---
title: "Solution for flash drive mounting as read-only"
date: 2013-09-29
forum: Hardware
---

### Post by Halfling Rogue on 2013-09-29
Had an 8.0 GB SanDisk flash drive, formatted as FAT32, that's been working fine with both Ubuntu and Windows for a long while. After attempting to clean it of some files (and accidentally deleting the .Trash folder in the process), the drive suddenly started refusing to mount in anything except read-only mode. GParted did not allow for reformatting for some reason, NTFS Config couldn't find the device, and reformatting the partition with Disk Utility didn't seem to get rid of the problem.

After some fiddling, the following process worked (all using Disk Utility):

1) Unmount the drive.
2) Delete the main partition/volume of the drive.
3) Format the drive itself, without any partitions ("Don't partition").
4) Create a new FAT volume on the drive.
5) Remount the drive.

Of course, this wipes out all files still remaining on the drive, so make sure to copy them or take them off via Windows before applying those steps. Hope this helps anyone else who runs into the same problem!

---

### Post by mörgæs on 2013-09-30
I saw that you tried to mark the thread 'solved', which is appreciated. The best way however is to use the option in Thread Tools.

---

