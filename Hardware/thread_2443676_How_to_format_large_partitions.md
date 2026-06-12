---
title: "How to format large partitions?"
date: 2020-05-18
forum: Hardware
---

### Post by bandmaster2 on 2020-05-18
I am new to Ubuntu.  I just installed Ubuntu Desktop 20.04 to a computer I put together with some used and new parts.  I want to create a Media Server slash NAS on the home network so I can cut the cord on the TV.  I managed to get Ubuntu Desktop installed on a 500GB SSD after disconnecting the data drives I had installed.  (The computer would not label the SSD as the first drive.)   I reconnected the 6 TB and 3 TB data drives but I can't get them to format with the full size of the drive available.  Each time I try I can only get 2.2 TB of free space available on each drive after creating a partition, formatting and mounting the drives.  What I am not understanding, I must be missing something stupid that I am not doing right?  I need the full 6 TB for media file storage and 3 TB for file backups.  Thanks for any help you can give me!

I plan to install Channels DVR and Plex to handle the media files and Synology Drive to back up files from my PC and laptop.

Dave S.

---

### Post by yancek on 2020-05-18
Is your Ubuntu install UEFI on a GPT drive and are the drives you are referring to GPT?  Did you create partitions on them?  Are these new drives which have never been formatted or used?  What filesystem are you attempting to use and what software are you using to try the format?

---

### Post by bandmaster2 on 2020-05-18
I did the standard install of Ubuntu.  They are all brand new hard drives, the motherboard, CPU, GPU and RAM are used.  Ubuntu formatted the SSD to FAT32 bootable on installation and it shows it mounted at /boot/efi and partitioning as MBR.  I made one single 6 TB and one single 3 TB partition on the data drives and formatted them in FAT 32, because I will use them with both Ubuntu and Windows.  They show partitioning as GPT.  But each drive only shows 2.2 TB of free space.

Dave S.

---

### Post by TheFu on 2020-05-18
MBR partition tables only support 2TB or so.  For larger disks, GPT must be used.  

Also, when you format each partition, use ext4 unless you have a specific reason to use something else.  Being new, ext4 is fast, stable and a reasonable choice.  Would be worth knowing that more advanced, enterprise level, storage management is available on your ubuntu box, for free.  i would say much better and certainly more flexible than Synology offers for the cost of cheap hardware.

What lead you to Channels DVR?  No problem trading money for time, but $80/yr seems steep for TV.  TV is extremely locality specific.  

Lots of people use TVheadend or mythtv or Plex+DVR service.   All those solutions seem really complicated to me.

it was an itch for me. Wrote a few scripts to record shows based on regex patterns, but my tuners are on the network and "recording" is just saving a file from an HTTP location.  Without a gui, simple things often remain simple.


update: i see you used fat32.  Bad idea for all sorts of reasons.   Use ext4.  Other computers can access the storage over the network using a number of different methods.

---

### Post by bandmaster2 on 2020-05-18
> **TheFu said:**
> MBR partition tables only support 2TB or so.  For larger disks, GPT must be used.  

Also, when you format each partition, use ext4 unless you have a specific reason to use something else.  Being new, ext4 is fast, stable and a reasonable choice.  Would be worth knowing that more advanced, enterprise level, storage management is available on your ubuntu box, for free.  i would say much better and certainly more flexible than Synology offers for the cost of cheap hardware.

What lead you to Channels DVR?  No problem trading money for time, but $80/yr seems steep for TV.  TV is extremely locality specific.  

Lots of people use TVheadend or mythtv or Plex+DVR service.   All those solutions seem really complicated to me.

it was an itch for me. Wrote a few scripts to record shows based on regex patterns, but my tuners are on the network and "recording" is just saving a file from an HTTP location.  Without a gui, simple things often remain simple.


update: i see you used fat32.  Bad idea for all sorts of reasons.   Use ext4.  Other computers can access the storage over the network using a number of different methods.


Interesting info, but none of it helps me solve my issue...

---

### Post by TheFu on 2020-05-18
> **bandmaster2 said:**
> Interesting info, but none of it helps me solve my issue...

FAT32 doesn't like large partitions.   
> Maximum sizes
The FAT32 boot sector uses a 32-bit field for the sector count, limiting the maximum FAT32 volume size to 2 tebibytes (approximately 2.2 terabytes) with a sector size of 512 bytes. The maximum FAT32 volume size is 16 TiB (approximately 17.6 TB) with a sector size of 4,096 bytes.[40][41] **Windows operating systems through Windows 10 only create new FAT32 volumes up to 32 GB in size**, however. 

Using FAT32 is a bad idea for over 64G partitions.  There will always be little issues  if using non-native file systems.  Use ext4 or some other native linux file system for the best solution.

---

### Post by bandmaster2 on 2020-05-19
Yes, I figured that out for myself earlier.  When I formatted the drives I chose the greater than 2.2 TB option.  Oh well, that didn't work out so well.  I deleted the drive partitions and reformatted my media drive to ext4 and my backup drive to ntsf.  Now I have the total disk space available on each.  I am still playing and experimenting with no real data, so I can always delete the partitions again and redo them when I finally learn what the hell I am doing.

Dave S.

---

### Post by ajgreeny on 2020-05-19
I hope you still have Windows  available to you somewhere as NTFS partitions that develop problems can not easily be repaired or have chkdsk  run on them using Linux so you could become stuck there eventually.

---

### Post by bandmaster2 on 2020-05-19
> **TheFu said:**
> What lead you to Channels DVR?  No problem trading money for time, but $80/yr seems steep for TV.  TV is extremely locality specific.  

Lots of people use TVheadend or mythtv or Plex+DVR service.   All those solutions seem really complicated to me.


I can't get over the air TV worth a damn where I live, too close to the moutains.  I had DirecTV then FIOS and they both have gotten way too expensive.  With Channels DVR I can sign up for YouTubeTV (with local network channels) and Philo TV and use Channels DVR to logon onto all those channels using my credentials and create a complete channel guide to surf the channels.  Plus all of those channels can be recorded on the DVR.  I might use Plex to organize and serve all my other media files.  We'll see if Channels DVR can organize my files to my satisfaction, if not I'll add Plex to do it.

Dave S.

---

### Post by bandmaster2 on 2020-05-19
> **ajgreeny said:**
> I hope you still have Windows  available to you somewhere as NTFS partitions that develop problems can not easily be repaired or have chkdsk  run on them using Linux so you could become stuck there eventually.

Yes, I will be networking with my Windows 10 PC and laptop.  The backup drive will also be accessed by several other out of network Windows PC's, so that's why I set it up as ntsf.  I'll be experimenting this week and if Windows can connect with the ext4 drive well enough I will reformat the other drive to ext4 as well before I transfer the real data files to it.  Like I said before, I am new to Linux and am not sure what it can do yet. 

Dave S.

---

### Post by Holger_Gehrke on 2020-05-19
The problem is that the File Allocation Table has a maximum size. Even if you use the maximum number of sectors for a cluster - the smallest unit of storage that can be assigned to a file - you'll end up with a file system with a size of around 2 TiB with the rest of the partition unusable. With modern disks that have a sector size of 4KiB you could in theory have 16TiB partitions, but AFAIK this Linux doesn't do this (probably because for other filesystems native to Linux the larger sectors are split up since the logical block size around which a lot of file systems are designed is 512 bytes per block).  Take a look at this article in [Wikipedia]("https://en.wikipedia.org/wiki/File_Allocation_Table"), the sidebar gives all the limitations of the variants of the FAT-formats.

Holger

---

### Post by TheFu on 2020-05-19
> **bandmaster2 said:**
> Yes, I will be networking with my Windows 10 PC and laptop.  The backup drive will also be accessed by several other out of network Windows PC's, so that's why I set it up as ntsf.  I'll be experimenting this week and if Windows can connect with the ext4 drive well enough I will reformat the other drive to ext4 as well before I transfer the real data files to it.  Like I said before, I am new to Linux and am not sure what it can do yet. 

Dave S.

Sounds like you have a plan to increase the comfort level and for the TV stuff.  Use Samba to make Linux storage available to Windows machines.  Some defaults in the protocols have changed recently on both the Windows and Linux sides, so a few careful options may be needed.  Name resolution changed on the Windows side for network sharing which seems to be another issue those client machines experience.  But if you have an internal DNS or just use avahi names {hostname.local} with your Ubuntu desktop systems, it should work.  

Here's a thread about Win10 clients accessing Ubuntu Storage using samba. 
[https://ubuntuforums.org/showthread.php?t=2434383](https://ubuntuforums.org/showthread.php?t=2434383)  

For pure data, NTFS is fine, if a little slower.  For real backups of Unix stuff, NTFS is a terrible choice for multiple reasons.  Sharing non-native Linux file systems like NTFS brings added complexities that are a hassle.  For example, NTFS doesn't support the Unix permissions model, so permissions for every directory and every file must be the same and will be set only through mount options.  This is a huge limitation for a multi-user system.  

Linux is still multi-user even if you only setup 1 userid.  Probably want to have your login userid, plex, and whatever userid the TV recording stuff runs under in a shared group so they can write to storage equally.  That group should be forced for all the data storage that gets shared. None of this is hard, but coming from Windows where file permissions are extremely lax, you'll need to adjust.  In Unix systems, which is every popular OS in the world today, except 1 (cough), file and directory permissions are the core technique for security.  No way around that.

---

### Post by SeijiSensei on 2020-05-19
> **bandmaster2 said:**
> I made one single 6 TB and one single 3 TB partition on the data drives and formatted them in FAT 32, because **I will use them with both Ubuntu and Windows**.
That only applies if you are dual-booting Windows and Linux.  If you're planning on using these drives to share files with Windows machines, then you should format them all with ext4 and run Samba on the Linux box as TheFu suggests.

---

