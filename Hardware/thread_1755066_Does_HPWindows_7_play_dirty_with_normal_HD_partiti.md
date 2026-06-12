---
title: "Does HP/Windows 7 play dirty with normal HD partitioning practices?"
date: 2011-05-10
forum: Hardware
---

### Post by thinkren on 2011-05-10
Last year, I bought a Presario CQ62-225NR running 64 bit Windows 7 Home Premium.  With the recent release of Natty, I’ve decided to take the plunge and try out the Unity interface.  In preparing the hard drive for dual booting Ubuntu, I shrunk the C: Windows partition using Disk Manager and deleted the D: RECOVERY partition. 
 
The 200mb hidden SYSTEM boot partition and the 100mb E: HP_TOOLS partition were untouched.
 
So far so good.  I now have an unallocated block of free space roughly 140 GB in size between the Windows Partition and HP_TOOLS partition.  Disk Management shows the three remaining partitions to be healthy.
 
However, after I boot into the Gparted live-CD, I’m presented with a small mess.  Every partition is lite up with caution signs.  A new partition that doesn’t appear under Disk Manager has popped up out of nowhere. And all the labels have now been shifted.
 
In short, before partitioning:
 
/dev/sda1; ntfs; SYSTEM; 199mb; boot
 
/dev/sda2; ntfs; [no label]; 286.29gb

/dev/sda3; ntfs; RECOVERY; 11.5gb

/dev/sda4; fat32; HP_TOOLS
 
After partitioning, as reported by Gparted:
 
/dev/sda1; ntfs; SYSTEM; 992.5kb --- {Warning:Unable to read the contents of this file system!  Because of this some operations may be unavailable.  The cause might be a missing software package.  The following list of software packages is required for ntfs file system support: ntfsprogs.}

/dev/sda2; ntfs; [no label]; 199mb; boot --- {Warning: unable to read the contents of this file system!  Because of this some operations may be unavailable.  The cause might be a missing software package.  The following list of software packages is required for ntfs file system support: ntfsprogs.}

/dev/sda3; ntfs; HP_TOOLS; 156.68gb --- {Warning: ntfsresize v2.0.0 (libntfs 10:0:0)  Failed to startup volume: invalid argument.  ERROR(22): Opening '/dev/sda3' as NTFS failed: Invalid argument. The device '/dev/sda3' doesn't have a valid NTFS.  Maybe you selected the wrong partition?  Or the whole disk instead of a partition (e.g. /dev/hda, not /dev/hda1)?  This error might also occur if the disk was incorrectly repartitioned (see the ntfsresize FAQ).  Unable to read the contents of this file system!  Because of this some operation s may be unavailable.  The cause might be a missing software package.  The following list of software packages is required for ntfs file system support: ntfsprogs.}

Unallocated; 141.11gb

/dev/sda4; fat32; [no label]; 103.34mb --- {Warning: Can't open /dev/sda4: No such file or directory.  Cannot initialize 'H:'  mlabel: Cannot initialize drive  dosfsck 3.0.9 (31 Jan 2010)  dosfsck 3.0.9, 31 Jan 2010, FAT32, LFN  open: No such file or directory  Unable to read the contents of this file system!  Because of this some operations may be unavailable.  The cuase might be a missing software package.  The following list of software packages is required for fat32 file system support: dosfstools, mtools.}
 
I have no idea how to interpret these results.  The whole point of repartitioning was to free up one of the 4 primary partitions for the use of Ubuntu.  If Gparted is to be trusted, it appears Windows 7 has for unspecified reason conjured up a new first partition and carefully hidden that fact from normal processes.  Appearance-wise, nothing has changed in Windows.  I can still boot the machine normally and do all the computing I did before with no ill effect.  But I’m back to square one with all partitions occupied and no room for Ubuntu.  
 
I took the precaution of saving a disk image with Clonezilla before starting this adventure.  Though the computer can run Windows just fine right now, I may choose to find out soon if the stored image can properly restore everything.  Then I’ll have another go at repartitioning the HD to get Ubuntu installed.  However before I do so, can anyone shed some light on what happened and tell me how to avoid the same results?

---

### Post by uRock on 2011-05-10
Duplicate thread here [http://ubuntuforums.org/showthread.php?t=1755070](http://ubuntuforums.org/showthread.php?t=1755070)

Thread Closed

---

