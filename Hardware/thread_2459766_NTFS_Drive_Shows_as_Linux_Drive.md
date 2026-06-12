---
title: "NTFS Drive Shows as Linux Drive"
date: 2021-03-25
forum: Hardware
---

### Post by Ronco Pizatto on 2021-03-25
I have an external 1TB USB HDD that I use for backup.

I decided to try a restore for the first time with RedoRescue
I booted with a RedoRescue Flash drive and my external drive plugged in.

My computer booted fine but I couldn't access the backup drive.

I ran fdisk -l and got the following

Device         Boot Start       End             Sectors     Size      Id   Type
/dev/sdb1        2048        234440703 234438656   111.8G 83   Linux

The size should be more than 111.8G for a 1 TB drive
The type should be NTFS

I've tried various things with Disks and gparted
I also tried ntfsfix

No change in the drive's problem.

I use Ubuntu 18.04 on a Lenovo 510s i3 desktop computer

Your help would be greatly appreciated.

---

### Post by yancek on 2021-03-25
Has this hard drive previously shown more than one partition including at least one with an ntfs filesystem on at least one partition?

---

### Post by TheFu on 2021-03-25
If you just copied files from Linux to some NTFS partition, that isn't really a backup.  Backups retain owner, group, permissions, ACLs, and xattrs. Often, those are equally, if not more important than the actual data.

I suspect you are only seeing the Linux partition because something on the other drive isn't working or the ntfs-utilities aren't part of that rescue distro.  Perhaps using a normal Ubuntu ISO which includes the expected file system utilities would work better?  I always use a Try Ubuntu-Mate ISO on a flash drive for any system recovery work.  It has almost all the tools pre-installed, including dm-crypt and the most popular Linux file systems.  If some file system that I need isn't supported, it is jsut an **apt-get install ....** away to load it.  For example, exFAT and F2FS aren't there by default.  It think ntfs and vfat (fat32) are included, along with ext2/3/4 support.

---

### Post by Ronco Pizatto on 2021-03-25
I may have done some good with the repair software but the drive still won't mount.
Disks now shows "NTFS-Not Mounted" but there's still unexpected parameters.

Disks shows partition 1 of 120 GB and 880 GB free space.
Shouldn't patiton 1 include the free space in its size?
This drive came as a single partition of 1 TB. 
Disks "Check file system" says it is not damaged.

-- Ronco
The Disks Mount Symbol when clicked doesn't mount the drive.

Can you suggest some diagnostics so I can give you more info?

---

### Post by TheFu on 2021-03-25
If the NTFS was last used on Windows, it is very possible that the Windows OS didn't correctly "close" the file system.  Linux won't mount it if left that way.  Connect it to Windows and be 100% certain to "eject" the drive.  Shutting down Windows is not sufficient. By default, Windows leaves file systems mounted even if shutdown is requested.

---

### Post by Ronco Pizatto on 2021-03-25
Thanks to TheFu and yancek for your thoughts.

I have all manner of backups on this drive.
A few Disk Images, a few Clonezilla images, RedoRescue images and all my data drive files.
It would be a pain to make them again.

I tried the drive on a Win10 system but I couldn't get a drive letter associated with the drive.
However, I'm not very familiar with Win10 since I've only used it on other people's systems.
I could be missing something.

I also tried the drive on a different Ubuntu 18.04 system but got the same result.
The drive light blinks when I plug it in and the drive shows in Nemo & Nautilus but there is no access.
Disks says its not mounted which is easy to believe according to its behavior.

I'll try booting an Ubuntu 20.04 live flash drive and see if that does any better. I'm not too hopeful on that.

---

### Post by TheFu on 2021-03-25
To fix NTFS problems, use Windows.  That's the bottom line.
There are lots of tools on Windows for dealing with NTFS.  On Linux, we only have reverse-engineered software that tries hard, but isn't written by the team who created the file systems ... cough .... Microsoft.

scandisk, chkdsk, are Windows tools. Start with those.

---

### Post by Ronco Pizatto on 2021-03-25
Thanks. I forgot about the software I used way back in the WinXP days.
I'm glad its still around.
I'll also try the Win10 Disk Management software.

---

### Post by yancek on 2021-03-26
> Shouldn't patiton 1 include the free space in its size? 

Output from tools such as fdisk will show the drive and partition sizes in sectors and you can see the amount of space used and unused on any partition with various other Linux tools.  There is a difference in free space/used space on a partition and unallocated space outside the partition.  You indicate the drive was originally an ntfs filesystem with one partition.  Your fdisk output now shows only one partition which has a Linux filesystem.

This would not happen automatically so you must have created that partition with the Linux filesystem so how you did that would be useul information.  As mentioned above, if you have an ntfs partition used on windows, a windows OS such as windows 10 will hibernate rather than shutdown and a Linux OS will not mount an ntfs partition which is hibernated as there is too much risk of data loss.   

>  I tried the drive on a Win10 system but I couldn't get a drive letter associated with the drive.

That is definitely not a good sign.  Windows of course, does not assign drive letters to non-wndows partitions such as Linux but should assign a drive letter to any windows filesystem partition.  You need to continue trying to access the partition using windows tools.  Good luck.

---

### Post by Ronco Pizatto on 2021-03-26
The problem started when I booted with a Redo Rescue flash drive and the usb backup drive plugged in during boot.
Then Redo Rescue generated an error when I tried to restore a backup.
After rebooting in Ubuntu and using Disks and gparted I noticed that the boot flag was enabled. I unchecked it.
Redo uses some form of Linux

It's kind of ironic that all my computer systems are fine but my backups are in jeopardy.
At this point I'm ready to partition, reformat the drive and make my backups again.
Fresh disk images are good I suppose.  

Thanks for your help yancek

---

### Post by TheFu on 2021-03-26
> **Ronco Pizatto said:**
>  At this point I'm ready to partition, reformat the drive and make my backups again.
Fresh disk images are good I suppose.  

Pro Tip: Don't use NTFS for Linux data this time.

---

