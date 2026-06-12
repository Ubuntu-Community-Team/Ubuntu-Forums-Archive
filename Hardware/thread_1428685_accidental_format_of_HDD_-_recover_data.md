---
title: "accidental format of HDD - recover data"
date: 2010-03-13
forum: Hardware
---

### Post by rockhoppe7 on 2010-03-13
Hi, did a foolish thing, hope someone can help me.

I was trying to put a boot image on my USB flash drive stick (using USB Startup Disk Creator in Koala 9.10).  

The program told me I should format the flash drive before making a startup disk.  I read the warning that the flash drive would be erased and I had read the man pages and help files that told me to be careful not to choose the wrong drive.  

Then I carefully chose the wrong drive - and pressed Format on my 500GB Western Digital MyBook USB backup drive.

I quickly realised what I'd done (about 2 seconds later) and did the first thing I could think of which was pull out the USB cable (maybe 5-7 seconds).  I think I also pressed Cancel on the USB Startup Disk Creator process as well.  By this time it had already produced an error message (something like 'cannot format this drive') so maybe it's that dialog that I remember OKing.  This error message is what makes me think I can maybe recover my data.

Now my MyBook USB drive can't be seen by the system.

Is there any way to recover the data on the disk?  Maybe I only erased the partition table (or something) and the data is still sitting there unseen?

Because it's a USB drive it's not listed in fstab - is there a permanent record of it somewhere in the filesystem or does ubuntu dynamically mount it if it's present on the USB port?  I don't even know this.

I'd be really grateful for any help - thanks

---

### Post by IcarusR on 2010-03-13
Important, first do a copy of entire hdd, at low level with something like dd. 
Then if you muck things up you can at least go back to square one & try again. One can never have too many backups !!


Try testdisk & photorec

[http://www.cgsecurity.org/wiki/TestDisk]("http://www.cgsecurity.org/wiki/TestDisk")

[http://www.cgsecurity.org/wiki/PhotoRec]("http://www.cgsecurity.org/wiki/PhotoRec")

Also there are a lot of good utilities for mbr on Hirens Boot CD if you can find a copy of it.

All the above are free.

Active Partition Recovery (dos or win version) is not free. Free version works only will not write changes to hdd, so try it first & if finds problem then buy.

[http://www.partition-recovery.com/]("http://www.partition-recovery.com/")

This is why I always unplug all drives I can before any format & double check details. 
As my father always said 'measure twice, cut once !'

---

### Post by rockhoppe7 on 2010-03-18
Well, I downloaded and ran TestDisk, but no luck - I'd obviously nuked my backup drive pretty successfully!  Luckily it was only my backups that were on it, so I made a new partition and backed up my data again.
Thanks for your help

---

### Post by jason10 on 2010-04-30
I did exactly the same thing as rockhoppe7, except I didnt unplug my drive in the middle of the format.  The format only took about 1.5 seconds and my 750gb drive is now blank.  Im all about backups but I only have the one drive of that size so thats where all my music was and i have no backups for that at all..  The drive is fine, it mounts just fine and reads 700GB of free space, FAT32.  

Ive been reading a lot about test disk and other utilities but my question is this..  what exactly is it that i am wanting to do here?  I know the files are still (mostly) there but just listed as free space.  Am I hoping to simply recover the table that knows where the files are, and then everything will be happy again?  or do i want to scan the whole drive and reassemble the files from the mess of dead space?  which one of those things is it that test disk does?  If i just want to recover the table, what is that file called?  Im not entirely sure what im doing and i dont want to do the wrong thing and screw it up worse than i already did.

also, test disk kind of confuses me.  i can probably figure out how to use it, but im still not sure what to do..  = /

..help?

---

### Post by srs5694 on 2010-04-30
jason10,

The word "format" is so ambiguous in this context that it's unclear precisely what you did. Chances are you did one of two things:


[list]
[*]You created a new partition table, thus making your original partitions inaccessible. In this case, testdisk *may* be able to recover your original partition table by locating the markers that indicate where each partition originally began on the disk. (Sometimes this task is complicated by leftover data from previous partitionings of the disk.)
[*]You created a new filesystem on an existing partition, thus rendering all the data within the partition inaccessible. In this case, the task is harder. You *may* be able to recover most or all of your data with [PhotoRec,](http://www.cgsecurity.org/wiki/PhotoRec) but you'll probably have to wade through a lot of individual files. This will be a much tougher recovery job.
[/list]


As background to the preceding summaries, know that disks are *partitioned* (split into contiguous groups of sectors, typically one to a dozen or so per hard disk). Each partition holds a single *filesystem* or other data structure (such as swap space). The partition table defines where partitions are, and it's fairly vulnerable to accidental erasure. If the partition table is erased, though, the filesystem itself may remain intact, in which case re-creating the partition table undoes the damage. Filesystems, OTOH, are more complex data structures that help you locate individual files via filenames and a hierarchy of directories (aka folders). If a filesystem is erased (which can take just a fraction of a second to many minutes, depending on the filesystem used, the filesystem creation options, and the size of the partition), it becomes very hard to recover the individual files that had been stored in the filesystem, although most or all of the data may still be on the disk.

---

### Post by jason10 on 2010-05-01
well..  I used the Ubuntu USB disk creator to format the drive (by accident) so im not sure what exactly that program does when it formats, but it took no time at all.  The drive had just one partition on it, and I dont clearly recall but Im pretty sure it was NTFS.  Now its FAT32.  I ran a windows gui recovery program on it (without making changes) called r-undelete and it only found a few files..

?rtstub.exe, ?shtdwn$.req, ?RT.exe, and mrt.exe._p

are any of these of any interest to me?  ..google searching doesnt make me feel like they are =/  screenshot attached.

thanks for the help so far

---

### Post by waldherrvonbirnbaum on 2012-04-03
PhotoRec works just amazing. It recovered everythink from my 8GB flashcard.
[http://www.cgsecurity.org/wiki/TestDisk_Download](http://www.cgsecurity.org/wiki/TestDisk_Download)
There is even a linux-version of it.
:guitar:

---

