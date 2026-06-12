---
title: "Ubuntu creates partitions on its own= can't mount HD"
date: 2012-10-13
forum: Hardware
---

### Post by Windowsdefector on 2012-10-13
*clears throat* Hello there! I'm brand new to these parts and especially Linux...
I have installed Ubuntu 12.04 and been running it for the past month. I love it! Recently though I stumbled on some issues...
I bought a new internal harddrive (WD Caviar Black Series 1 TB) and that is the reason I am here... There is a problem mounting the drive.

At first, I plugged in the drive and it showed up in BIOS, Ubuntu started up but there was no visible unit mounted on "computer" (as it does with my other units).
I googled the issue and tried to find a way to list disks that are physically connected in hopes of getting a confirmation the actual disk is working (as I said; it does show up in BIOS). 
But that didn't work so well as the suggestions usually involved typing commands in the Terminal... Which I am not that fond of.
I got this idea that in this Ubuntu version (don't know if earlier versions have it too) I have installed everything seems to have a GUI. You can actually bypass the terminal for doing system maintenance.
So I searched for programs via the Hub and found "disk utility" and there was my disk listed but not mounted!
 
I came to conclusion that it just needed a formatting to show up (I even think that is the way it works in Windows, right? but why?). 
So I formatted the disk (filesystem NTFS) and voila! I could mount the disk and all was right with the world. Then I rebooted the system and it all crashed. And this can be repeated infinite number of times and you get the same results. 
After the reboot however: the disk (I named it 1TB) was still visible on "computer" but it had a duplicate oddly enough. I tried accessing both and I get an error msg reading "unable to mount 1TB". 
I went back to "disk utility" and there I see the disk divided to  5 different "pieces"/partitions: unallocated space, NTFS filesystem and so on.    
I don't know why this happens, but this is the problem.
The formatting reverts back and changes to unallocated space among others.


I should mention:  usage of this HD is for storage of data only.


Here is an error msg that might be of help: 
ERROR MOUNTING VOLUME details:
[I]Error mounting: mount exited with exit code 12: NTFS signature is missing.
Failed to mount '/dev/sdb1': Invalid argument
The device '/dev/sdb1' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?[/I]
This happens when I try to mount the disk in "disk utility" after I have rebooted the computer.


I have attached 3 print screens - before and after, so you can see for yourselves.

Picture 1: I use "format drive" and choose "don't partition" - the HD is broken in to 5 pieces= causes error messages.
[http://i50.tinypic.com/2f0d5i1.png](http://i50.tinypic.com/2f0d5i1.png)

Picture2: this is after I have formatted the drive. 
[http://i48.tinypic.com/14se0i9.png](http://i48.tinypic.com/14se0i9.png)

Picture 3: this is after I have formatted the volume > NTFS
[http://i49.tinypic.com/2rvzsk4.png](http://i49.tinypic.com/2rvzsk4.png)

PS. I have searched and searched this problem and some had the same problem but with different circumstances I believe, so I made my own thread.

---

### Post by grahammechanical on 2012-10-13
First this explains why a disk needs to be formatted before it can be used in any operating system.

[http://en.wikipedia.org/wiki/Disk_formatting]("http://en.wikipedia.org/wiki/Disk_formatting")

Note this:

> Formatting a disk for use by an operating system and its applications involves three different steps

Please read about the three steps.

All you need to do now is to partition it into one partition.

Usually we partition the drive and then format the partition.

> Partitioning is the process of writing information into blocks of a storage device or medium that allows access by an operating system. Some operating systems allow the device (or its medium) to appear as multiple devices; i.e. partitioned into multiple devices.

I think that you will find that every hard disk has to have at least one primary partition. There can (at the present time) be up to four primary partitions but no more. Therefore, if we want more than four partitions we use one of the possible four primary partitions to create one Extended partition and in that Extended partition we can create many more logical partitions.

Regards.

---

### Post by oldfred on 2012-10-13
I think you formatted the drive not the partition.

NTFS requires a valid PBR or partition boot sector that has info on the start & size of partition similar to the info in the partition table (and data must match). 

If sharing with Windows, NTFS is fine, but if for use with Linux better to have a LInux format like ext4. With NTFS you need a Windows install to be able to run chkdsk. Ubuntu schedules its filechecks every 40 or 60 reboots, but Windows does not automatically run any filechecks, but still should have chkdsk run occasionally and before errors appear.

gparted & fdisk instructions:
[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

---

### Post by Windowsdefector on 2012-10-18
> **oldfred said:**
> I think you formatted the drive not the partition.



I formatted the partition as well BUT I did not choose Master Boot Record when I formatted the drive. I thought since I won't use it for anything else than data storage then it wouldn't need it. But I guess not.  However I do not understand why it created several partitions on its own after a reboot.
Anyway, I partitioned the whole drive and chose MBR and it works! Thanks.

I have a few questions though...
Why won't Linux and a storage drive partitioned as NTFS work well together? It seems to  be working fine to me.
It even warns when you format as NTFS that these two are not a good combination.
What is the worst that can happen? Does the data become corrupt? 
If so: when does it happen? Where does it happen?  How does it happen?
You see, the thing is I have a boatload of data on old harddrives, I planned to transfer everything to this disk but I want to know why I am warned against transferring it to a drive with a NTFS file system and if I do go ahead with it, when can I feel safe when the task is done? Or can everything seem to be fine at first and the next day I can't access the data?

What if you use the storage device on computers with both Windows and Linux? If you use EXT4 then it won't work  [well] with Windows and if you use NTFS it won't work [well] with Linux.  That seems to be tough.

EXT4, the Linux format, how compatible is that with Windows? 
EXT4 instantly takes up to 50GB. Why? That isn't encouraging.

---

### Post by oldfred on 2012-10-18
NTFS is ok if you want to share data with Windows. And much better than FAT32. But only use for data not anything else. And only when sharing with Windows so you can occasionally run chkdsk from Windows. 

But NTFS does not support Linux ownership nor permissions, so you cannot use it with LInux system or User configuration files as then they lose essential settings. 

I would never use any of the Windows drivers that may work with some of the Linux formats. Again the issue is often ownership & permissions which can lead to lots of issues.

Also in Linux the default is to reserve 5% of the diskspace for the superuser (this can be adjusted using tune2fs. See man page for tune2fs. 
Should always leave the reserve for system partitions but if only data you can reduce it. It is to prevent system from crashing if almost full.

---

