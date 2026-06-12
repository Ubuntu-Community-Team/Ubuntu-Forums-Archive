---
title: "Cannot access ntfs drive"
date: 2016-04-12
forum: Hardware
---

### Post by jgw on 2016-04-12
This is not quite as simple as the title suggests.  My wife uses windows and wanted me to update her system from xp to windows 10.  What I did was buy her a new drive and put windows 10 on that.  Then I added her old xp drive to the system so all her data files, etc. could be easily copied to the new windows 10 drive.  

What happened is that I got everything installed and running and, for some reason, windows 10 decided to mess with the old xp drive (I have no idea why).  So, now, windows 10 can no longer access the drive.  I now have that drive on this machine (as external).   Here is the drive in question:
    Disk /dev/sde: 1000.2 GB, 1000204886016 bytes
    255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
    Units = sectors of 1 * 512 = 512 bytes
    Sector size (logical/physical): 512 bytes / 512 bytes
    I/O size (minimum/optimal): 512 bytes / 512 bytes
    Disk identifier: 0xa47c60fb
    Device Boot      Start         End      Blocks   Id  System
   /dev/sde1   *        2048  1953523711   976760832    7  HPFS/NTFS/exFAT

Disks (program) told me, whilst the machine was connected to this (ubuntu) machine as an external:
   Error mounting /dev/sde1 at /media/greg/8CFDD4F1FAA97A97: Command-line `mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000,dmask=0077,fmask=0177"
   "/dev/sde1" "/media/greg/8CFDD4F1FAA97A97"' exited with non-zero exit status 14: The disk contains an unclean file system (0, 0).
   Metadata kept in Windows cache, refused to mount.
   Failed to mount '/dev/sde1': Operation not permitted
   The NTFS partition is in an unsafe state. Please resume and shutdown
   Windows fully (no hibernation or fast restarting), or mount the volume
   read-only with the 'ro' mount option.
   (udisks-error-quark, 0)

I tried to run gparted but that program got stuck on this drive and has been trying for about 10 minutes to figure it out (to no avail).  If I remember correctly it said that the entire drive was a master boot record single partition 

I suspect there are all sorts of programs to mess with a hard drive.  My fear is whatever I do I will loose the data and that would be a real bad idea.   

Any thought would be appreciated on this one.

---

### Post by weatherman2 on 2016-04-12
I'd run a Windows chkdsk /f on the drive.  But first, in Ubuntu, I would check the S.M.A.R.T. status and Attributes of the drive.  Install GSmartControl and check the S.M.A.R.T. Attributes.  Any highlighted in red or pink?  Those are the the ones that are suspect.  (Ignore all of the messages about "pre-failure" - just a type of attribute.)  If you booted Ubuntu live from CD or USB to do the above, then you will need to enable the "universe" repository" first to be able to install GSmartControl (and then you must be online to install gsmartcontrol).

If the disk isn't failing and there are no suspect S.M.A.R.T. Attributes, then I'd go ahead and run chkdsk.  ("Error check" in Windows 10.)  If you have a Windows boot CD, you can boot that on any system this XP disk is connected to and run chkdsk that way.

---

### Post by yancek on 2016-04-12
The error reported "The disk contains an unclean file system (0, 0)" means that you left windows hibernated and did not fully shut it down.  If you do not fully shut it down, you will not be able to mount the partition or access it from and Linux system because the system could be easily damaged.  Hibernation is the default setting for windows 8 and newer so you have to turn off anything related to fast startup, fast boot and hibernation and fully shut down windows before trying again.

As to why you can't access the xp partition from windows, that's another question and maybe the suggestions above will help.

---

### Post by jgw on 2016-04-15
The first thing I need to do, I think, is to clean up the unclean file system.  I cannot mount this drive because of the unclean file system thing.  Does anybody have any idea how I can take care of this problem?   I have also found out that I can access this drive in gparted magic from the ultimate boot disk so I assume there are programs that I can use, hopefully, to try and save the files on that drive.

Thank you................

---

### Post by yancek on 2016-04-15
You can't repair the proprietary ntfs filesystem partition from Linux.  Boot into windows and run chkdsk

---

### Post by oldfred on 2016-04-15
In Windows be sure to turn this off.
 Fast Startup off (always on hibernation)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)

I do not know if this works in Windows 10 or not:

 Windows 7 unmount
[http://windows.microsoft.com/en-us/windows/mount-dismount-drive#1TC=windows-7](http://windows.microsoft.com/en-us/windows/mount-dismount-drive#1TC=windows-7)

---

### Post by jgw on 2016-04-15
I have found out some stuff.  I can, for instance, load and mount the offending drive with: mount -t ntfs-3g -o ro /dev/sdb /media/500gb (name of the drive)   When I do this I can also find my file system.  I tried copying some stuff but something that might be 3 gb large is suddenly 150gb.  What I have done is to take a 500gb drive, delete everything with dd if=/dev/zero of=/dev/sdX  bs=512  count=1.  the problem, now, is that it deleted EVERYTHING!  (no problem it had nothing important).  So, I went to both disks and gparted and tried to create a new partition.  Both programs failed.  Gparted, for instance, tells me to see the details to see what happened, the problem is that there are no details.  Disks, on the other hand tries to create a partition but it too fails.  I beat my head against a wall for a bit and then hit on types.  I have found, for no reason I can figure out, that whenever I try and give it a partition, irregardless of the type (I was shooting for ntfs but ext4 won't work either).  My plan is to use this drive to copy files to and then deal with them.  

The drive itself looks like:
=== START OF INFORMATION SECTION ===
Model Family:     Seagate Barracuda 7200.10
Device Model:     ST3500830A
Serial Number:    5QG1F0V0
Firmware Version: 3.AAD
User Capacity:    500,107,862,016 bytes [500 GB]
Sector Size:      512 bytes logical/physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ATA/ATAPI-7 (minor revision not indicated)
Local Time is:    Fri Apr 15 17:59:08 2016 PDT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

---

### Post by oldfred on 2016-04-15
Windows will probably give you grief.
If Windows is hibernated it has the file structure saved. And that sets a flag on drive somewhere which may still be the issue.
And when you boot Windows it may try to restore structure, but not sure it can restore all the files. 

When Windows sets hibernation or needs chkdsk on a NTFS partition, the Linux NTFS driver will not mount it. You can force a read only mount which it seems you did. And you dd command just erased partition table, but not data on drive.

---

### Post by jgw on 2016-04-16
as far as I can tell gsmart control can remove all the hibernation stuff.  The only problem with that is that it will lose anything that happened before the hibernation.  I don't really care about that as the damage was done when it was just setting there during a windows 10 installation (that went dandy, except for the shutdown and its now working (my wife tells me))  I need the stuff that was on the drive before whatever happened to the drive so it might even be a good thing.  

Now, of course, I have a whole new problem.  I took out a 500gb drive to move whatever I can get out of the problem drive.  I decided to just put a new partition on it to get rid of whatever was on it.  The problem is that I cannot put a new partition on that drive.  When I try for a new partition (after deleting all remaining) gparted tries and finishes, no errors, no details, nothing happens.  When I try disks it tells me that it cannot deal with the file type (its always a different type) in my messing around I found a bug report that said gparted sometimes confuses types (it was old and doubt its pertinent).  Anyway, yet another mystery.

I am currently researching moving files off a corrupt drive.  I could run chkdsk against the problem drive (the drive was formatted ntfs) but fear losing files.  I also suspect that my fear is misplaced and any files destroyed by chkdsk are probably screwed anyway.  Any suggestions on this one would be appreciated.

---

### Post by oldfred on 2016-04-16
I might first try testdisk and possibly its deeper search to see if it see files. Then you get full file names.
If not you can use photorec which just scans drive for anything that looks like a file. You only get extensions so it can take a long time to figure out file names. (It took me weeks, as it also recovered all my deleted files & I had to compare many copies with an older backup.) And it is slow as it has to scan entire drive. And requires lots of space on another drive as it copies all data to that drive.
[URL="https://help.ubuntu.com/community/DataRecovery"]https://help.ubuntu.com/community/DataRecovery
[/URL] [URL="http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step"]http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step
[/URL]
 [http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step)

[URL="https://help.ubuntu.com/community/DataRecovery"]
[/URL]Some say for NTFS, Windows scan tools work better.
An alternative Windows data recovery program is Recuva -- and it is free
[http://ubuntuforums.org/showthread.php?t=2247461](http://ubuntuforums.org/showthread.php?t=2247461)
[http://ubuntuforums.org/showthread.php?t=2236951&p=13086950#post13086950](http://ubuntuforums.org/showthread.php?t=2236951&p=13086950#post13086950)
You could start by using Recuva -- to see what it finds. If it doesn't work, you should then try RecoverMyFiles -- to see what it finds.
NTFS file recovery suggestion by Mark Phelps (not free but works)
[http://ubuntuforums.org/showpost.php?p=12490412&postcount=4](http://ubuntuforums.org/showpost.php?p=12490412&postcount=4)

[URL="https://help.ubuntu.com/community/DataRecovery"]
[/URL]

---

### Post by jgw on 2016-04-16
OK, I am currently getting files off the problem drive.  I found [http://www.hecticgeek.com/2013/01/mount-windows-8-partition-ubuntu-hybrid-boot/](http://www.hecticgeek.com/2013/01/mount-windows-8-partition-ubuntu-hybrid-boot/) which explained howto use 'disks' to take care of the hiberdrive.sys file.  After that finished I was able to r/w the disk, see the folders, and start copying files.  Disks also tells me that the problem drive is about to fail in bright red <G>   It looks like I am going to copy something like 400gb and it tells me I still have a bit over 3 hours before it finishes.  Hopefully it will get done and I will have what I need.  

Thank you for all the help - it IS appreciated!

---

