---
title: "Harddisk Addition"
date: 2023-11-17
forum: Hardware
---

### Post by amraeknsyah on 2023-11-17
Hi everyone ! 

I've added a 1TB hard drive to my computer, but the ubuntu 23.10 system only reads my 256GB SSD. How can I add or activate my Harddisk so that it can be used in the ubuntu system? 

Thankyou!

---

### Post by tea for one on 2023-11-17
Does your new disk have a partition table and, at least, one partition?

---

### Post by TheFu on 2023-11-17
> **amraeknsyah said:**
> Hi everyone ! 

I've added a 1TB hard drive to my computer, but the ubuntu 23.10 system only reads my 256GB SSD. How can I add or activate my Harddisk so that it can be used in the ubuntu system? 

Thankyou!

You have a few questions to answer, before making any use of any new storage.
[LIST=1]
[*]What is the purpose?
[*]What types of data will it hold?
[*]What OSes need local, directly connected, access?
[*]How will you backup everything on the new disk?
[/LIST]

Purpose:
Is it for an OS, personal files, media files, documents?
Will it be shared with others? How?  Over the network?  Using some specific sharing tool?  As network storage?  Sneaker*net?

Types of Data:
This directly related to the file system to be used and where it needs to be mounted.  Media files will likely need to be shared on the LAN.  Documents probably don't need to be shared, unless you have some "cloud" solution like Nextcloud/Owncloud or just push the data to a cloudy, privacy-stealing, provider, like Google.

Which OSes:
If only Linux will be connected to the storage, you'll want a native Linux file system. If you might need to add more storage in the future, using a volume manager. like LVM, can make future additions much easier.  If the computer dual-boots with some other "commercial" OS (cough), then you may want NTFS as the file system.  NTFS doesn't support the full permissions model used by all Unix systems and it isn't necessary for network access by Windows. Also, Linux tools can't really fix NTFS corruption problems, when they arise.  In short, stay with a native linux file system, like ext4, unless you have an extremely good reason to choose something else.

Backups:
My stance is that any data worth holding is worth having a backup.  If I can't backup the primary data, then I have no business keeping it.  Considering that 2TB USB HDDs are less than $40 these days, it makes little sense NOT to have backups.

So, it is very likely you will want to start over with this new storage.  The steps are:
Using gparted, 
[LIST=1]
[*]create a new GPT - GUID Partition Table
[*]create at least 1 primary partition, sized however you like, but ensure it is aligned on a sector boundary if this is a spinning HDD. For SSDs, it doesn't matter.
[*]format the new partition to ext4
[*]Add a LABEL to the new ext4 partition - no spaces in that name.  This LABEL will make it easier to mount AND will have meaning to all us humans. I'll assume you used a label of "1TB" and ext4.
[*]create a mount point to hold this new ext4 file system.  I'll assume this is /d/1TB for now.   ```
sudo mkdir -p /d/1TB
```
[/LIST]

Gparted stacks things to be done into a queue, so don't forget to press the "Apply" button and let it run.  For 1TB, the format will be the longest part and should finish in about 30 seconds.

Edit the /etc/fstab, using **sudoedit /etc/fstab**, adding this line to the bottom:
```
LABEL=1TB    /d/1TB    ext4    defaults,nodev,nosuid 0   1
```
Add 1 extra line to the file. This is a good habit to avoid 30 yr old bugs in parsing text files. Always have 1 extra, blank line, at the bottom of ever config file.  Mounting ext4 storage is much easier than NTFS.

Mount the storage, **sudo mount -a**
and it will be available in /d/1TB now and forever.

The owner for new storage is always root, so if you want to make it available to your userid, run this command exactly to have your userid take ownership:
```
sudo chown -R $USER:$USER   /d/1TB
```

Now, you can create directories and put files into it.  If you want to use it for documents that are easily access from your HOME directory, you can create a directory for that and make a symbolic link from your HOME to it.

If the system has multiple users and you'd like to share access to this new storage with those others, you'll probably want to create a subdirectory for each other person (I'd use their userids) and give them ownership.

I think that's about it.

If gparted can't see or modify the storage, then there are issues, perhaps firmware in the storage needs to be upgraded to be compatible with the disk controller on your motherboard.  If that's the situation, you'll need to look for problems in the system log files related to this storage device.

---

### Post by amraeknsyah on 2023-11-17
Not yet

---

### Post by amraeknsyah on 2023-11-17
ahh it's cool information, i will try it 

Thankyou!

---

