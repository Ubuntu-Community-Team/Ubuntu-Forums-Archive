---
title: "Where is the format command?"
date: 2017-02-10
forum: Hardware
---

### Post by Milambar on 2017-02-10
My old laptop died, but the hard disk was salavageable. So I mounted it into my Ubuntu machine, and was able to retrieve all the files I want to keep off it.

Now I want to reformat it, completely, and just use it as a backup drive. Its too slow for regular use as its only 5400rpm, but it IS a large capacity drive (750GB), so would be ideal for storing backups.

However, I can't find the format command, and I've searched the repositories with apt-cache.

Please don't tell me to install gparted, the machine does not have a keyboard, mouse or monitor attached to it. I do all tasks via a shell via ssh.

I want to basically, "format /dev/sdc -t vfat", in order to completely format the drive to the vfat filesystem, but so far, I have not been able to find the format command. There are a bunch of "guides" which are all assuming a completely clean disk, and jump straight in at partition creating and mounting, but none that actually tell you how to format the drive first.

Could someone please point me in the right direction without assuming I am using a graphical front-end to anything.

---

### Post by DuckHook on 2017-02-11
There is no command called "format" in Linux. Please have a look at:```
man mkfs.fat
```If trying to make vfat, be sure to use the *-F 32* flag.

Neither FAT nor VFAT are very robust for data preservation purposes like backups. EXT4 is much better. Even EXT2 is superior. But if journaling is not needed, you are still better off using EXT4 and just disable the journal.

---

### Post by Milambar on 2017-02-11
And once again, you are assuming a blank disk.

"mkfs is used to build a Linux filesystem on a device, usually a hard disk partition...."

Not only are you skipping ahead and assuming that the disk is blank, you are also assuming that it is pre-partitioned. That does not help me erase the disks current data and reformat it to be completely clean for re-use. 

Thank you, but it appears that you either didn't completely read or understand the question.

I do not want to welly in a new linux partition onto the disk, thereby ending up with 3 partitions (Windows, WinRecovery, Linux), I want to ERASE the entire disk, ending up with just ONE partition, for data storage.

As for the next comment you made, Ive used ext4 disks with Linux before, and when they go bad, they still go bad, and the "journal" is no help in recovering the data. So using a journalled filesystem seems entirely pointless.

So I ask again, how do I reformat the entire disk? Can linux even do this, or do I have to hook it up to a windows machine?

It currently has two partitions that are not needed or wanted, but secure erasure is not necessary. Partition /dev/sdc1 is Windows, partition /dev/sdc2 is WinRecovery. I want it to be reformatted, and have just ONE partition, and I don't even care what its named. Ideally it will be of the VFAT filesystem, so that there will not be any problems in mounting the drive in a windows machine in future if needed, NTFS also considered but I have heard that Linux can have issues when writing to NTFS disks, which is why I specified vfat as it seems to be the most portable filesystem.

---

### Post by steeldriver on 2017-02-11
The command line equivalent of **gparted **is called **parted**

```

NAME
       GNU Parted - a partition manipulation program

SYNOPSIS
       parted [options] [device [command [options...]...]]

DESCRIPTION
       parted  is a program to manipulate disk partitions.  It supports multi&#8208;
       ple partition table formats, including MS-DOS and GPT.   It  is  useful
       for  creating space for new operating systems, reorganising disk usage,
       and copying data to new hard disks.


```

I'm not sure it supports VFAT, but it certainly should support FAT32

Start with

```

sudo parted /dev/sdb print

```

to see the current partition layout - then you can remove and create partitions as desired

---

### Post by Milambar on 2017-02-11
I don't want to EDIT PARTITIONS. I want to reformat the disk.

Can linux really not reformat disks?

---

### Post by steeldriver on 2017-02-11
OK

LINUX is NOT Windows.

If you expect to do everything you used to do on Windows, using the same commands you used on Windows, then yes you will have to "hook it up to a windows machine"

Otherwise, you can use parted to remove any existing partitions, and create a single new one - thereby "ending up with just ONE partition, for data storage"

---

### Post by Dennis N on 2017-02-11
> I want to ERASE the entire disk, ending up with just ONE partition, for data storage.

1) use gparted (partition editor), select the right disk, then from the menu, choose **Device > Create Partition Table >** and make a selection (ms-dos or gpt). This wipes out (erases) the existing partitions and leaves unallocated space.


2) You then can make partition(s) to use from the unallocated space - at least one partition. Again, use gparted. From the menu, **Partition > New** and fill in the details in the dialog box. In this process, you select how to format the partition. Technically you format a partition, not a disk.

---

### Post by DuckHook on 2017-02-11
@OP Making allowances for your frustration, I shall attempt to further explain:

[LIST=1]
[*]*steeldriver* is correct: the ability to *edit* partitions is the same as the ability to *destroy* and *create* them.
[*]The superiority of ext4 is not in data *recovery*, but in *speed*, *security*, data *integrity* and filesystem *efficiency*. As only one example, the better structure of ext filesystems (vs FAT) is why ext filesystems almost never need defragmentation whereas Windows filesystems have to be defragged practically every week. In your case, if you decide to use rsync for backup purposes, a FAT filesystem will fragment from the second time it is used into a sodden mess whereas an ext filesystem will not. You will also run into problems with permissioning because a FAT filesystem does not even understand that concept. As already stated, if you don't want the slight performance overhead of journalling&#8213;which, by the way, is not useful for disk failure so much as for filesystem corruption caused by, say, brownouts&#8213;then just turn it off:```
tune2fs -O ^has_journal /dev/sd?? #where ?? is your drive and partition number
```
[/LIST]
@Dennis N

OP has stated that HDD resides in a headless CLI-only server. Gparted is not available to him.

---

### Post by Milambar on 2017-02-11
Someone on freenode finally gave me an answer.

"You can't reformat them as people understand from a windows perspective. On that point, you are correct, Linux cannot reformat hard drives. What you need to do is first, use parted or fdisk to DELETE the existing partitions. Then use fdisk or parted to create a new partition spanning the entire disk, then finally use mkfs.vfat to create a vfat file system on the new partition. The last step is probably the closest you will get to "reformatting" under Linux, but the end result is the same."

I guess it comes down to just a terminology difference.

He gave me a step by step walkthrough using parted, which made the process a lot clearer.

Thank you to everyone who tried to help, and sorry if I got a bit fustrated there.

---

### Post by DuckHook on 2017-02-11
> **steeldriver said:**
> &#8230;you can use parted to remove any existing partitions, and create a single new one - thereby "ending up with just ONE partition, for data storage"

> **DuckHook said:**
> &#8230;*steeldriver* is correct: the ability to **edit** partitions is the same as the ability to **destroy** and **create** them.

> **Milambar said:**
> Someone on freenode finally gave me an answer&#8230;:confused:

How does that explanation differ from the ones given here?

**EDIT**

OK. Did not see your postscript.

---

### Post by Milambar on 2017-02-11
Apologies to Steeldriver,  I did not see his post until after I had posted the solution that I was provided with on freenode. I wasn't ignoring it.

---

### Post by DuckHook on 2017-02-11
Happy for you that it all worked out in the end.

*Please mark thread **solved** using *Thread Tools* in the top toolbar for the benefit of others searching for solutions*.

---

