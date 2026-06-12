---
title: "Help recreating partition on table"
date: 2019-11-03
forum: Hardware
---

### Post by jimbob32 on 2019-11-03
So, I have been using ubuntu/linux off and on for the last 10 years or so. Recently, while working making a new flash drive, I managed to delete a partition off the table, and I am hoping someone can help to get it back in full working order. 
Previous experience tells me that this is just a partition table entry, and no data has actually been deleted.  Therefore I can create a partition on the table, and as long as I don't do any sort of mkfs or formatting, the data should still be there.

Original partition sda2 was 832 GB ntfs with win10 install on it.  This is an approximate size.  All I had was the output from the last "df -h" I had run.  If it had been a regular "df" I would have had the exact size and probably wouldnt be here, but alas, I am left with a size rounded to nearest GB.

I was able to create a partition using cfdisk and my approximate size+ a few gb to make sure it was not too small.
I now have /dev/sda2 of 840.4GB which I was able to mount, and the files are there.  It is currently mounted as read only, and I am using it as such. But it seems to work ok.
I am guessing this will cause problems long term if I don't get the correct block size for the original partition, and resize my new sda2 accordingly.

In order to try to recreate the correct block size, I tried following the directions here:
[https://www.simplylinuxfaq.com/2018/11/how-to-recover-accidentally-deleted-disk-partition-linux.html](https://www.simplylinuxfaq.com/2018/11/how-to-recover-accidentally-deleted-disk-partition-linux.html)

In the  "step 2" I was unable to  get usable output from their instructions. 
Upon "dumpe2fs /dev/sda2"  Instead of getting a nice readout of start and end block numbers I am getting "Bad magic number in super-block while trying to open /dev/sda2  Couldnt't find valid filesystem superblock.   /dev/sda2 contains a ntfs file system"

Now further down on that page there is directions for if that error comes up using info from /etc/lvm/backup/ and "vgcfgrestore" but the file I have in there only includes info on "sde"  nothing on sda, so I was unable to get any farther.


So my main concerns are:
1.  will I run into problems using this approximately sized partition if I try to boot windows (which was on the origial sda2)
2.  If I create another partition in the free space after sda2 will I run into problems installing an os/booting off of it?
3.  Are there any other issues with using it as is besides a few unusable GB on the hd?

Please note: The disk in question is an ssd (1tb samsung 860 evo) I do not currently have the space to copy all the files off the partition, then start fresh, or I would be working on that already.  
If that is really the only option I may consider adding some old drives to backup the data, or possibly even purchasing a new 1tb hdd, as they can be had for under $20 these days, and I wouldn't mind an extra TB for storage etc, and I was planning on a fresh install of windows anyways for other reasons, which is how I ended up in this mess.  
BUT 
I really should be retiring hdd's not adding more, and a 1tb ssd is a little more expensive.

If anyone can help me get the correct block size info/file to use with vgcfgrestore, or if there is another way to do it, please share!

Thank you!

---

### Post by yancek on 2019-11-03
> I now have /dev/sda2 of 840.4GB which I was able to mount, and the files  are there.  It is currently mounted as read only, and I am using it as  such. But it seems to work ok.

How are you using it?  Does that mean accessing it from your Ubuntu install to look at/read files?  Filesystems are often mounted read-only when there is some corruption to the filesystem.  You might try run chkdsk from a windows tool which you should be able to download from the microsoft site or some other reliable web site for windows.  You can't fix this from Linux.

Did you run the command exactly as suggested, with spaces, quotes, etc.?

> dumpe2fs /dev/sda2 | egrep "Block size|Block count"


I had the same error on an external drive last week.  Difference was that mine was a Linux filesystem and run fsck on it a few times enabled me to save most of the data.  This was a very old drive and it is totally dead now and I doubt that is the problem in your case.  Yours is an ntfs filesystem so you could try chkdsk from a windows tool.   Also, the suggestions at the link you were reading discuss LVM and most users do not install using LVM.  Did you?  If not, don't use the recommendations/suggestions regarding LVM.

I don't have an answer to what would happen if you boot windows or create another partition after it but I would try chkdsk.  Good luck.

---

### Post by TheFu on 2019-11-03
Everything I know how to do would have happened BEFORE the issue.  Backup of the data.  Backups of the storage configuration.  Working after the fact is hard.

Did you happen to try parted's rescue mode? From the parted manpage:
```
              rescue start end
                     Rescue  a  lost  partition  that  was located somewhere
                     between start and end.  If a partition is found, parted
                     will  ask  if you want to create an entry for it in the
                     partition table.

```I've never used it.

Nobody knows "any other way", so nobody can make claims about that, but they might know 1 method.  Heck, you can always go in with a hex editor and manually setup everything.  I can't, but perhaps you could?  That would be "any other way" to fix it too.

You've already broken the 1st rule of data recovery - never touch the original storage.  The first step, always, is to clone all the bit to other storage and never touch the original.

Imagine you'd done this BEFORE it was needed:
```
sudo parted -lm | tee /root/partition-table-backups
```
How tiny is that file?  It would have been easy to backup with your other data, right?  It can be used to exactly recreate a partition table. Handy, right?

You mention vgcfgbackup   vgcfgrestore.  Those are for LVM.  Yet, no other mention LVM?  Was LVM being used or not?  LVM tools aren't exactly useful if LVM isn't being used.  However, if LVM is being used, then /etc/lvm/backup/ is where that data is placed.  Do you have access to it?  I include /etc/ in all my backups.  It is tiny, just 33MB.  Most of the data/configs in /etc/ aren't needed during a fresh install, but having it for reference is always helpful, I've found.  Actually, I just keep these:
```
sudo pvs | tee /root/pvs.stuff
sudo vgs | tee /root/vgs.stuff
sudo lvs | tee /root/lvs.stuff
lsblk -o name,size,type,fstype,mountpoint | tee /root/lsblk.stuff

```
to capture LVM overview information. Include it in your backups, so it is available, later, when needed.

All this has to be done BEFORE it is needed.  Sorry.

---

### Post by hk42 on 2019-11-03
The deleted partition should appear as "free space" using fdisk /dev/sda
I would try to create a primary NTFS partition(ID=7) in that free space.
Record the new partition table and try to mount the new partition.
Don't format anything.
HTH

---

### Post by oldfred on 2019-11-03
Windows at minimum will require chkdsk. It has inside the partition boot sector, info on size that must match partition table size info. 
Chkdsk will update that info.

In addition to parted rescue it testdisk. 
If you know approx start & end, even if only form surrounding partitions parted rescue seems to work well and bit easier than testdisk.
Testdisk finds all the old versions of partition table, so when restoring you have to be sure to choose correct or non-overlapping sets of partitions.

[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
Used parted rescue
[https://ubuntuforums.org/showthread.php?t=2362656](https://ubuntuforums.org/showthread.php?t=2362656)
[http://ubuntuforums.org/showthread.php?t=2315405](http://ubuntuforums.org/showthread.php?t=2315405)
backup partition table before any changes, so you can get back to current if changes not correct
sudo sfdisk -d /dev/sda > PT_sda.txt
So you know sectors:
sudo parted /dev/sda unit s print

---

### Post by jimbob32 on 2019-11-03
OK first off, thank you all for the suggestions. The important thing thing to take away from this is to regularly back things like this up.  Config files are tiny, and could have saved me a lot of trouble.  Luckily there is nothing super mission critical on this partition.  Just a windows install and a few odds and ends.  Most all of anything really important on older storage hdd's (at least as a redundancy).  

@[COLOR=#000000]yancek yes using it from linux (very minimally) but the data appears to be there.  Generally ime ntfs partitions with a windows install get mounted as read only by default. At least on my install which is 18.1.  Thinks the windows install was hibernated (which prevents it from mounting normally) Although windows was not hibernated.  So the fact it is mounted read only is no surpise here.  Everything seems as normal for the most part.  But I have not tried booting windows.  
When you say try chkdsk, I am guessing you mean from a separate unaffected windows installl?
I do not have one handy at the moment, so it would mean booting windows off of the drive prior to running chkdsk.

The output from that command is the same with or without the egrep.  Anything involving "dumpe2fs /dev/sda2" gives the same output.
Regarding LVM, now that I think about it, I have used LVM in the past, but not in this install.   I should have caught that, before even trying those things. 

@TheFu
I will be sure to include all of /etc in all future backups, and ill make a script to run those commands and backup to files.  No LVM on this install, my bad.
As far as breaking the first rule of data recovery, that is one of my questions, should I just focus on trying to backup the data up directly from this point, and start fresh?
Again, nothing super mission critical on this drive. I have already backed up anything I really needed that bad immediately upon gaining access to the data.  Read only  is fine for backups :)
If it was something mission super mission critical on that drive, I wouldn't even have tried to fix it myself without extracting all usable data from a data recovery tool.
In this case its a lot of gb of data, but nothing that cannot be replaced.

@HK42
That is exactly what I did before posting this.  Unfortunately there was no partition directly after this one on the drive, so the partition I made is not of the exact right size.  It is about 8gb larger, but it seems to be working.   I am trying to see if there is a way to correct the size, so I can coumfortably boot off it.

@oldfred
I am looking into trying parted rescue.  I wish I would have seen that first.   The issue I see is that 1, there was free space following the partition, so no clear point to create the partition to.   This is the reason I created the partition just a few gb larger, as a safe guess. 
Sounds like CHKDSK may work.  If I do boot windows I will try that.  Or if I am able to put the drive in another computer running windows I might try it that way.  Same goes for testdisk.  They both seem like good ideas 
I am guessing chkdsk will resize the ntfs filesystem to fit my 840.4gb partition I made?
Or is that what testdisk will do?  


For parted rescue though, I am guessing I should have done that before creating the approximately sized partition that I did?   if so it is easily deletable/recreatable at this point by backing up the current partition table.  So I can try that.

For anyone who has used parted rescue, do I want to do it with the partition table in the state it was before I created the partition? ie. delete the partition I made?  Or will it resize the partition I made to fit the filesystem?   I am guessing that I would want to delete the slightly oversized partition I made before using parted rescue?

Keep in mind I do know where the partition started, as there was a partiton before sda2, which i'm sure is a large reason why I was able to access the files, but after it was free space, so if parted rescue is depending on data from a surrounding partition on both sides, I do not have them both.

Thank you all![/COLOR]

---

### Post by oldfred on 2019-11-03
I also have not used parted rescue.
But the posts that have, seem to indicate that you only need approximate start & end sectors just outside of partition. So end of previous partition and end of drive should also work.
Testdisk shows old partitions, not sure if it still uses the old CHS, not sectors which makes it a bit more difficult to translate size.

Now that you created new partition, I might think parted rescue would find that. Testdisk may show both versions, old one as deleted.

---

