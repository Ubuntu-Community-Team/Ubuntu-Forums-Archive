---
title: "What is going on with my partitions?"
date: 2012-12-29
forum: Hardware
---

### Post by jacox on 2012-12-29
I recently bought a new server (N40L). I also bought 3x3TB drives for  storage. 



Now the drives got shipped before the server did, so I  installed two of them in my Windows PC to shuffle some existing data  around.
 The drives are both formatted with NTFS and show up in Gparted. My  problem is that they seem to both have 2 partitions and then two blocks  of unallocated space.



I've attached a picture for reference.
 Using the Disks app
[http://img221.imageshack.us/img221/7322/screenshotfrom201212300.png](http://img221.imageshack.us/img221/7322/screenshotfrom201212300.png)
[URL="http://img221.imageshack.us/img221/7322/screenshotfrom201212300.png"]
[/URL]
 Using Gparted:
[http://img213.imageshack.us/img213/7322/screenshotfrom201212300.png](http://img213.imageshack.us/img213/7322/screenshotfrom201212300.png)
 

Both of these drives have the two partitions with the two blocks of  unallocated space. I can't format them because they both have my media  collection on them.


 Is there something wrong, or is this just how Ubuntu lists them?


Here is a screenshot of another drive that is formatted with NTFS,  displays no errors or warnings in Gparted, and automounts at startup. This drive was formatted within Ubuntu, the two partitioned drives were formatted to NTFS using Windows 7.



Working NTFS drive showing in Gparted.
[http://img547.imageshack.us/img547/3939/screenshotfrom201212301.png](http://img547.imageshack.us/img547/3939/screenshotfrom201212301.png)
[URL="http://img547.imageshack.us/img547/3939/screenshotfrom201212301.png"]
[/URL]
 Why are my other drives showing the way they are?

---

### Post by ahallubuntu on 2012-12-29
Is your Windows PC capable of using GPT-partitioned drives, so it can handle partitions larger than 2TB?

---

### Post by oldfred on 2012-12-30
There is another thread where a user formatted with Windows on a 3TB drive and is having issues. I think both Windows & Disk Utility seem to have issues with very large gpt drives, although they are supposed to work.

You have to use gpt partitioning if you want all 3TB as MBR(msdos) has a max of 2TB.

I think it best to create partitions with gparted or gdisk. But I am not sure if there are then any issues with NTFS formats when used with Windows. 

       MBR details including 2TiB limit and GPT link
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)

            GPT fdisk Tutorial -srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)

---

### Post by jacox on 2012-12-30
The disk i am having issues with was originally formatted to NTFS in Windows using the MBR partition table. Now that i'm using linux to manage the drives, i've realised that i should have used the GPT partition table from the start..

My situation is now this:

I have a 3TB NTFS drive with an MBR partition table full of media (2.6TB worth). I have a blank 3TB EXT4 formatted drive with a GPT partition table. The EXT4 drive has no issues and is mounted automatically at startup.

I want to copy all the data from the NTFS drive to the EXT4 drive, and then format the NTFS drive to EXT4. The problem is that it's copying at a pitiful 11mb/s! This will take 76 hours.

Is there a faster way to copy all of that data across?

---

### Post by oldfred on 2012-12-30
Do not know.

Are you using USB ports or have drives connected internally, since temporary connections.
NTFS is slower as it has to go thru fuse or is not a native drive, but I do not think it should be that slow.

---

### Post by jacox on 2012-12-30
I'm using internal SATA connections for all the drives.. 11MB/s is unacceptable.. What can i do?

---

### Post by oldfred on 2012-12-30
I do not know.

Sometimes different tools work differently, but the underlying NTFS driver is still the same. How is it mounted, defaults from Nautilus or fstab? But I do not know if that would make any difference. 

My backups are to a Linux formated partition and I use rsync. What are you using to copy data?

---

### Post by ahallubuntu on 2012-12-30
What version of Windows?  If you formatted your drive in Windows XP or an old version of Vista (without service packs), then you probably have misaligned partitions on an advanced format drive.  That could mean severe performance issues.

Newer versions of Windows and newer versions of Ubuntu automatically align partitions to avoid this problem; otherwise, there's a tool to align partitions to fix this problem, but it moves your data.  It makes sense to align your partitions on a newly formatted drive, before you copy any data to it - it's very quick. But there's no point in running an alignment tool after you have a lot of data - you might as well just spend three days and copy the data.

Linux's fuse driver for NTFS is CPU intensive and is slow for very large files.  11MBps does not sound too far off if you are moving very large (1GB+) files from an unaligned NTFS partition using Linux.  If you are using a machine with a slow CPU, that will slow things down as well.

---

### Post by jacox on 2013-01-01
The drives were all formatted using Windows 7. After much research and googling these type of speeds seem normal when copying huge amounts of data. It also seems to cause the mount.ntfs process to reach 100% CPU usage. 

I wish there was another day. Having to wait three days for data to copy across is ridiculous. I guess it's better than having no NTFS support at all though. I can't really expect to have kernel based NTFS support, not from Microsoft anyway.

Oh well..

---

### Post by jacox on 2013-01-01
I've figured it out!

I'm using Rsync to copy the data between both drives and the speed is incredible! So fast!

---

