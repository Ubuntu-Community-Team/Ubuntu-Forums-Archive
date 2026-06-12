---
title: "Problems with XFS file system on RAID 0"
date: 2008-09-23
forum: General Help
---

### Post by Gizmonty on 2008-09-23
I have set up a Myth TV backend on Ubuntu (64 bit) which has a 2TB RAID drive (2 striped 1TB drives). This has a single XFS partition and is set to be where the bulk of my video files, etc will be stored.

The problem I have been having is that as I am trying to copy my old files across to it (about 500GB of video files) it intermittently breaks. I get permission denied, input/output errors. I am no longer able to unmount or mount the drive and the only way I have found out of this situation is to reboot the entire system. After a reboot, the drive is back and works fine. I am usually able to copy quite a lot of files across before this happens (maybe 20GB or so).

I have found a few reports of similar sounding problems on various forums relating to XFS on RAID 5 but the discussions were a little too technical for me to make much sense of them.

Is this a known issue or do I just have a broken system?

Any help would be appreciated.

---

### Post by fjgaude on 2008-09-23
Have you even run a **fsck** check of the array? Or run **fdisk -l**?

---

### Post by Gizmonty on 2008-09-24
fdisk -l gives the following
[INDENT]
Disk /dev/md0: 2000.4 GB, 2000404348928 bytes
2 heads, 4 sectors/track, 488379968 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table[/INDENT]

If I run fsck on /dev/md0 it tells me that I need to run xfs_check
[INDENT]
fsck 1.40.8 (13-Mar-2008)
If you wish to check the consistency of an XFS filesystem or
repair a damaged filesystem, see xfs_check(8) and xfs_repair(8).[/INDENT]

If I run xfs_check I get an enormous amount of output like so

[INDENT]bad nblocks 10 for inode 1073742092, counted 1
bad nblocks 45009 for inode 1073742093, counted 1
bad magic number 0x4142 for inode 1610613024
bad magic number 0 for inode 1610613025
bad magic number 0 for inode 1610613026
bad magic number 0 for inode 1610613027
bad magic number 0 for inode 1610613028
bad magic number 0 for inode 1610613029
bad magic number 0 for inode 1610613030
bad magic number 0 for inode 1610613031
bad magic number 0 for inode 1610613032
bad magic number 0 for inode 1610613033
bad magic number 0 for inode 1610613034
bad magic number 0 for inode 1610613035
bad magic number 0 for inode 1610613036
bad magic number 0 for inode 1610613037
bad magic number 0 for inode 1610613038
bad magic number 0 for inode 1610613039
bad magic number 0x4941 for inode 1610613040
bad magic number 0 for inode 1610613041
bad magic number 0 for inode 1610613042
bad magic number 0 for inode 1610613043
bad magic number 0 for inode 1610613044
bad magic number 0 for inode 1610613045
bad magic number 0 for inode 1610613046
bad magic number 0 for inode 1610613047
bad magic number 0 for inode 1610613048
bad magic number 0 for inode 1610613049
bad magic number 0 for inode 1610613050
bad magic number 0 for inode 1610613051
bad magic number 0 for inode 1610613052
bad magic number 0 for inode 1610613053
bad magic number 0 for inode 1610613054
bad magic number 0 for inode 1610613055

... then a heap of output like

block 21/784682 expected type unknown got data
block 21/784683 expected type unknown got data
block 21/784684 expected type unknown got data
block 21/784685 expected type unknown got data
block 21/784686 expected type unknown got data
block 21/784687 expected type unknown got data
block 21/784688 expected type unknown got data
block 21/784689 expected type unknown got data
block 21/784690 expected type unknown got data
block 21/784691 expected type unknown got data
block 21/784692 expected type unknown got data
block 21/784693 expected type unknown got data
block 21/784694 expected type unknown got data
block 21/784695 expected type unknown got data
block 21/784696 expected type unknown got data
block 21/784697 expected type unknown got data
block 21/784698 expected type unknown got data
block 21/784699 expected type unknown got data
block 21/784700 expected type unknown got data
block 21/784701 expected type unknown got data
block 21/784702 expected type unknown got data
block 21/784703 expected type unknown got data
block 21/784704 expected type unknown got data
block 21/784705 expected type unknown got data
block 21/784706 expected type unknown got data
block 21/784707 expected type unknown got data
block 21/784708 expected type unknown got data
block 21/784709 expected type unknown got data
block 21/784710 expected type unknown got data
block 21/784711 expected type unknown got data
block 21/784712 expected type unknown got data
block 21/784713 expected type unknown got data
block 21/784714 expected type unknown got data
block 21/784715 expected type unknown got data
block 21/784716 expected type unknown got data
block 21/784717 expected type unknown got data
block 21/784718 expected type unknown got data
block 21/784719 expected type unknown got data
block 21/784720 expected type unknown got data
block 21/784721 expected type unknown got data
block 21/784722 expected type unknown got data
block 21/784723 expected type unknown got data
block 21/784724 expected type unknown got data
block 21/784725 expected type unknown got data
block 21/784726 expected type unknown got data
block 21/784727 expected type unknown got data
block 21/784728 expected type unknown got data
block 21/784729 expected type unknown got data
block 21/784730 expected type unknown got data
block 21/784731 expected type unknown got data
block 21/784732 expected type unknown got data
block 21/784733 expected type unknown got data
block 21/784734 expected type unknown got data
block 21/784735 expected type unknown got data
block 21/784736 expected type unknown got data
block 21/784737 expected type unknown got data
block 21/784738 expected type unknown got data
block 21/784739 expected type unknown got data
block 21/784740 expected type unknown got data
block 21/784741 expected type unknown got data
block 21/784742 expected type unknown got data
block 21/784743 expected type unknown got data
block 21/784744 expected type unknown got data
block 21/784745 expected type unknown got data
block 21/784746 expected type unknown got data
block 21/784747 expected type unknown got data
block 21/784748 expected type unknown got data
block 21/784749 expected type unknown got data
block 21/784750 expected type unknown got data
block 21/784751 expected type unknown got data
block 21/784752 expected type unknown got data
block 21/784753 expected type unknown got data
block 21/784754 expected type unknown got data
block 21/784755 expected type unknown got data
block 21/784756 expected type unknown got data
block 21/784757 expected type unknown got data
block 21/784758 expected type unknown got data
block 21/784759 expected type unknown got data
block 21/784760 expected type unknown got data
block 21/784761 expected type unknown got data
block 21/784762 expected type unknown got data
block 21/784763 expected type unknown got data
block 21/784764 expected type unknown got data
block 21/784765 expected type unknown got data
block 21/784766 expected type unknown got data


[/INDENT]

I didn't let xfs_check run to completion as I got the message.

What does all this mean? Have I set things up incorrectly? If so why am I able to read and write data to the disk most of the time? Should I just run xfs_repair? I'm sure there used to be a partition table on /dev/md0, otherwise how could I have created a file system there?

I hope someone can help.

---

### Post by fjgaude on 2008-09-25
Well, fdisk doesn't understand arrays... but you should have seen what each drive gave you.

I can't say what if anything you have done that is right or wrong. It certainly seems that the filesystem in not on the drives correctly.

You created the array, then added the filesystem, eh?

---

### Post by Gizmonty on 2008-09-26
This is what I get for the 2 drives that make up the array.


Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xef10e716

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1      121601   976760001   fd  Linux raid autodetect



Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5e923902

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      121601   976760001   fd  Linux raid autodetect


And yes, I created the array before adding the filesystem. That's the correct way to go about it, is it not?

---

### Post by fjgaude on 2008-09-26
Well, that all looks as it should. I can't think of anything more to suggest.

---

### Post by georgz on 2008-09-26
Are you accessing the array only from one Ubuntu version, or do you dual boot several Linux/Ubuntu versions and access the same array?

---

### Post by Gizmonty on 2008-09-30
I am only accessing the array from a single installation of ubuntu although I often log into it from another machine via ssh - I don't think this should make a difference.

---

