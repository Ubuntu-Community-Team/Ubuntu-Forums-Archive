---
title: "Editing number of sectors on a hard drive"
date: 2013-01-08
forum: Hardware
---

### Post by corwinspyre on 2013-01-08
Hello,

I have a 2.7tb (actual size) external hard drive.  Foolishly I defragmented it, and the defrag program set the size as 2.0tb, and now it won't mount.  Testdisk and gdisk show the problem explicitly

Here's the partition table (via gdisk):
> 
Expert command (? for help): p
Disk /dev/sdb: 4294967295 sectors, 2.0 TiB
Logical sector size: 512 bytes
Disk identifier (GUID): F5AD4340-C643-4839-8C26-24485B25FD93
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 4294967261
Partitions will be aligned on 8-sector boundaries
Total free space is 2014 sectors (1007.0 KiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1              34          262177   128.0 MiB   0C01  
   2          264192      5860532223   2.7 TiB     0700  


Here's the MBR info:
> 
Expert command (? for help): o
MBR disk identifier: 0x2D6E95FF
MBR partitions:
Number	 Boot	 Start (sector)	 Length (sectors)	Type
   1	    	            1	     4294967295 	0xEE

Disk size is 4294967295 sectors (2.0 TiB)


The problem is given:
> Expert command (? for help): v

Problem: partition 2 is too big for the disk.

Warning! Secondary partition table overlaps the last partition by
1565564962 blocks!
You will need to delete this partition or resize it in another utility.


If you take the last sector of 2.7tb, 5860532223, and subtract the number of sectors listed when it says 2.0tb, 4294967261, you're left with 1565564962, the precise amount the "partition table overlaps the last partition".

The problem is I can't figure out how to change the disk size (length) from 2.0tb to its actual length of 2.7tb.  I don't have a computer that supports EFI, meaning all my computers maxed it at 2.0tb, so I had to have someone else format it initially, and after that, it detected as 2.7tb on all my computers.  What this has meant is every program I've tried won't let me set the sectors past 4294967295 (2.0tb).  Does anyone know how to get by that roadblock?  Thanks!

---

### Post by tlhIngan on 2013-01-08
If I understand correctly, you are running a disk larger than 2 TB on a computer that won't support disks over 2 TB. I don't think there's a way to fix this. Your computer cannot see anything larger than 2 TB, so it will only see the first 2 TB of this disk.
You may format the disk on an EFI computer, that will format the disk to it's proper capacity, and that disk may be listed at it's proper size on your computer after that, but I doubt you will be able to access more than the first 2 TB of it.

---

### Post by corwinspyre on 2013-01-08
> **tlhIngan said:**
> If I understand correctly, you are running a disk larger than 2 TB on a computer that won't support disks over 2 TB. I don't think there's a way to fix this. Your computer cannot see anything larger than 2 TB, so it will only see the first 2 TB of this disk.
You may format the disk on an EFI computer, that will format the disk to it's proper capacity, and that disk may be listed at it's proper size on your computer after that, but I doubt you will be able to access more than the first 2 TB of it.

After I formatted it on a computer supporting EFI, I was able to see and use all 2.7tb of it on all of my computers.  Trouble only occurred after defragging, when the defrag program set the disk size to 2.0tb.  (Not having EFI supported is only a problem when it comes to wanting to use a 2+tb hard drive as a boot drive, whereas I'm using it just as an external drive for media.)

The only problem is because my computers don't support EFI, now that the drive is set at 2.0tb, programs I've tried to edit the number of sectors have built in checks to make sure you don't do something "stupid", such as setting the final sector as larger than the number of sectors it sees.  The problem is the latter is precisely what I need to do.  

So, I am hoping someone knows of program that will let me manually set the disk size (number of sectors) beyond what it sees as the reported disk size or knows another way to get by that.

---

### Post by sudodus on 2013-01-08
> **corwinspyre said:**
> After I formatted it on a computer supporting EFI, I was able to see and use all 2.7tb of it on all of my computers.  Trouble only occurred after defragging, when the defrag program set the disk size to 2.0tb.  (Not having EFI supported is only a problem when it comes to wanting to use a 2+tb hard drive as a boot drive, whereas I'm using it just as an external drive for media.)

The only problem is because my computers don't support EFI, now that the drive is set at 2.0tb, programs I've tried to edit the number of sectors have built in checks to make sure you don't do something "stupid", such as setting the final sector as larger than the number of sectors it sees.  The problem is the latter is precisely what I need to do.  

So, I am hoping someone knows of program that will let me manually set the disk size (number of sectors) beyond what it sees as the reported disk size or knows another way to get by that.
If possible, go back to the computer supporting EFI, where you formatted it the first time, and do it again. I guess that would be the easiest way to do it.

If you have backed up everything (or at least what is valuable) from the disk, you can also 'play' with some tools, and try to get around the 2 TB limit. In that case you can start with *fdisk* and ***sfdisk***. (Probably cfdisk won't let you do it.)

Read the manual page of fdisk carefully before starting
```
man fdisk
```

*Edit*: I suggest that you use a filesystem that needs no defragmentation, for example ext3 or ext4, or that you try with partition size less than or equal to 2TB

---

### Post by corwinspyre on 2013-01-08
> **sudodus said:**
> If possible, go back to the computer supporting EFI, where you formatted it the first time, and do it again. I guess that would be the easiest way to do it.

If you have backed up everything (or at least what is valuable) from the disk, you can also 'play' with some tools, and try to get around the 2 TB limit. In that case you can start with *fdisk* and ***sfdisk***. (Probably cfdisk won't let you do it.)

Read the manual page of fdisk carefully before starting
```
man fdisk
```

*Edit*: I suggest that you use a filesystem that needs no defragmentation, for example ext3 or ext4, or that you try with partition size less than or equal to 2TB

Thanks for your post!

Unfortunately I drove about 1000 miles for the holidays to see my family and used my brother's laptop to do the initial format, so that isn't an option.

I have over 2tb of files on the hard drive and no other drive larger than 2tb, so backing up or copying them off is not possible.  In other words, I need to fix it without reformatting or anything that would lose the data on it.  

fdisk doesn't support GPT.  gdisk is recommended when you run fdisk on a GPT drive, but it will not let me set the number of sectors beyond 2.0tib.  sfdisk has the same problem (having the same dev as gdisk).

---

### Post by sudodus on 2013-01-08
> **corwinspyre said:**
> Thanks for your post!

Unfortunately I drove about 1000 miles for the holidays to see my family and used my brother's laptop to do the initial format, so that isn't an option.

I have over 2tb of files on the hard drive and no other drive larger than 2tb, so backing up or copying them off is not possible.  In other words, I need to fix it without reformatting or anything that would lose the data on it.  

fdisk doesn't support GPT.  gdisk is recommended when you run fdisk on a GPT drive, but it will not let me set the number of sectors beyond 2.0tib.  sfdisk has the same problem (having the same dev as gdisk).

I would not tamper with any partitioning tool on a drive with important data without a good backup!!! So I suggest that you wait until you can get a drive, that is big enough for the backup, and start again.

Are there important files, that you cannot access now, because they are outside the 2 TB limit?

---

### Post by corwinspyre on 2013-01-08
> **sudodus said:**
> I would not tamper with any partitioning tool on a drive with important data without a good backup!!! So I suggest that you wait until you can get a drive, that is big enough for the backup, and start again.

Are there important files, that you cannot access now, because they are outside the 2 TB limit?

Buying a hard drive to copy the files over will not help because I don't have a computer supporting EFI to format it, so I would not be able to use it anyway.

I am willing to mess with the MBR, GPT, etc., to try to get this working.  There is no other option.  What I need is a program without safeties as mentioned earlier to let me put in the right sector count and such into the MBR.

I cannot access any files on the hard drive right now, whether before or after the 2tb limit.  The hard drive will not mount at all.

---

### Post by oldfred on 2013-01-08
If drive is over 2TB you cannot use fdisk, but can use gdisk or gparted. Fdisk family of tools only support MBR which max is 2TB.

       three Linux partitioning tools: the fdisk family [fdisk, sfdisk, and cfdisk], the libparted family [GNU Parted, GParted, Palimpsest Disk Utility, and several others], and the GPT fdisk family [gdisk and sgdisk]. 

GPT fdisk Tutorial -srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)

     repair gpt:
[http://www.rodsbooks.com/gdisk/repairing.html](http://www.rodsbooks.com/gdisk/repairing.html)
last partition overlaps backup partition table
[http://ubuntuforums.org/showthread.php?t=1956173](http://ubuntuforums.org/showthread.php?t=1956173)

    But you still may have issues with a BIOS/USB driver/ external drive cage that does not support large drives. Windows is supposed to support large drives, but XP does not work with gpt drives at all.

---

### Post by corwinspyre on 2013-01-08
> **oldfred said:**
> If drive is over 2TB you cannot use fdisk, but can use gdisk or gparted. Fdisk family of tools only support MBR which max is 2TB.

       three Linux partitioning tools: the fdisk family [fdisk, sfdisk, and cfdisk], the libparted family [GNU Parted, GParted, Palimpsest Disk Utility, and several others], and the GPT fdisk family [gdisk and sgdisk]. 

GPT fdisk Tutorial -srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)

     repair gpt:
[http://www.rodsbooks.com/gdisk/repairing.html](http://www.rodsbooks.com/gdisk/repairing.html)
last partition overlaps backup partition table
[http://ubuntuforums.org/showthread.php?t=1956173](http://ubuntuforums.org/showthread.php?t=1956173)

    But you still may have issues with a BIOS/USB driver/ external drive cage that does not support large drives. Windows is supposed to support large drives, but XP does not work with gpt drives at all.

They do indeed support GPT, but they will not let me edit the MBR to set the size past 2.0tib.  I have gone through those guides extensively.  I appreciate your help though!

---

### Post by sudodus on 2013-01-08
> **corwinspyre said:**
> Buying a hard drive to copy the files over will not help because I don't have a computer supporting EFI to format it, so I would not be able to use it anyway.

I am really sorry that you have this problem, and I really want to help.

It would be possible to make a clone (bit-to-bit copy) using low-level copying of the drive to another one of at least the same size. You can use ***dd*** or ***ddrescue*** to do that. And that would be a backup copy.

Those tools are very powerful but also risky. They do what you tell them to do without asking questions. So if you get it the wrong way, you will overwrite your data. (dd is nick-named 'disk destroyer')

---

### Post by oldfred on 2013-01-08
If Linux fdisk is working on your drive, you have converted it to MBR. And MBR has a maximum of 2TB.

Fdisk should just see the protective MBR and see one large partition as the entire hard drive with a gpt entry, where gparted or gdisk will show the gpt partitions on the drive. 

The main reason for the protective MBR is so fdisk and other older tools know drive is partitioned with gpt and do not corrupt it.

post this from parted & gdisk, change sda to whatever your drive is:

       sudo parted -l
sudo parted /dev/sda unit s print
sudo gdisk -l /dev/sda

---

