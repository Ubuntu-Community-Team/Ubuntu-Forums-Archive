---
title: "Formatting HD using Ext3 (for use with TV)"
date: 2021-08-26
forum: Hardware
---

### Post by Lappert on 2021-08-26
I'm using an old version of Kubuntu, but I don't think that's an issue here. I have a bunch of old drives I use to store video and play on my TCL Roku TV. One drive was formatted as Ext4 and it wasn't working. I'm not sure if it's the TV, Roku or the external drive dock -- Customer support for the TV was no help.

Most 2TB drives I have are formatted Ext3 or NTFS and work fine. One 3TB partitioned as Ext3 works fine. But this one is 3TB and Ext4, and not working. 

As the drive is itself a backup, I'm not worried about saving the files. So I bring up Gparted, (it's also on a USB external dock connected to my PC, not internal SATA), erase the old partition, tell it to create a new Ext3 primary partition (full disk). That went on for several hours and I don't know why. Usually when I purchase new drives, usually the partitioning and formatting take only a few minutes. I haven't had a full disk format take a long time since 1989 or so.

So why would it be that some drives partition almost immediately and this one (so far) is over 2 hours? Is there an alternative method I should consider? I also have KDE Partition Manager, but haven't tried it yet on this drive. And I seem to remember it can also be done from the command line, but I'm apprehensive about that.

Any help on this is appreciated. Thank you.

---

### Post by TheFu on 2021-08-26
You can use **gdisk** to do the partitioning and **mkfs** to create the file system(s)
It is very important that there be a GPT partition table on all HDDs over 2TB in size, but really, in 2021, all disks should have that.

I'm a little surprised that ext3/4 would work with any TV or Roku.  Every consumer video device that wasn't specifically Linux, like a raspberry pi, required fat32, exfat or NTFS in my experience.

According to [https://forums.roku.com/viewtopic.php?t=66910](https://forums.roku.com/viewtopic.php?t=66910), 
> The following USB drive formats are supported: FAT16, FAT32, NTFS and HFS+.

---

### Post by Lappert on 2021-08-26
Thanks, I'll look into it. The drive is on a USB eternal dock, so it probably won't show up for gdisk as of now it has no partition (a catch-22). I could temporarily put it on a SATA connection.

The TV docs say it will work with Ext3, and other Ext3 drives I have work OK. See [https://support.roku.com/article/230160368](https://support.roku.com/article/230160368)

[COLOR=#333333][FONT=GothamLight]"Roku devices support USB drives that are formatted with the FAT16, FAT32, NTFS, EXT2, EXT3, and HFS+ file systems."[/FONT][/COLOR]

Thanks for the tip on GPT. A few of the older drives are 10+ years old ... but they work. I suppose I could always go back to NTFS or fat32. As the drives are essentially archived video, it doesn't have to do a lot. Not looking to push the envelope with this; just readable.

At this point my prime concern is the time it takes to create a partition and/or format the drive. In my experience - at least for 20 years - creating a partition and formatting take only a few minutes. This was going on for over 2 hours until I cancelled the job.

Back in the real old days I remember 48 hours to do a low-level format, but that hasn't been the case for a long time. Is there a way to opt out of doing a complete drive scan?

Again, thanks.

---

### Post by Lappert on 2021-08-27
Update: I'm trying to do the same thing with KDE Partition Manager. I checked and the "unallocated" disk is a GPT partition. So I'm trying to create a new partition (no formatting yet)

So far - the first 25% happened almost immediately. Now it seems stuck on 25%, but I'm only 10 minutes into it. It does seem, like I noted above, that it's doing a full disk scan. Just last month I bought a 8TB drive; the process to create a new partition and format took only a very short time, a few minutes at most. So all this just doesn't make sense.

I think I'll leave it on overnight to see what progress happens.

Create a new partition (2.73 TiB, ext3) on &#8216;/dev/sdh&#8217; 
Job: Create new partition on device &#8216;/dev/sdh&#8217; 
Create new partition &#8216;/dev/sdh1&#8217;: Success

Job: Create file system &#8216;ext3&#8217; on partition &#8216;/dev/sdh1&#8217; 
Command: mkfs.ext3 -q /dev/sdh1

---

### Post by TheFu on 2021-08-27
That's great news about all the added file systems supported.

**gdisk** is a CLI tool.  It will create a GPT partition table just by being pointed at any disk device. It doesn't care if it is USB, SATA, eSATA, IDE, or even an empty file full of anything (or zeros).  In Linux/Unix, everything is a file ... so we can point tools at things that aren't necessarily exactly what is normally used, then use that new thing as if it was the device going forward. It is a very powerful idea.  Did you know that a directory is just a file?  Same for the mouse, keyboard, and nearly every other device connected to any Unix-like OS.  You don't really need to know this, but it does blow people's minds when they see it used.

The rest of this post is general in nature, probably not specifically helpful to your exact situation, since the hardware devices can only support what they support, until some future firmware updates happen.  I find it odd that Roku (a BSD OS, not Linux) supports ext2/ext3 at all.  I'd expect UFS support on BSD.

If you want nearly instant formatting, use LVM with EXT4.  I doubt this will work with any consumer hardware, since LVM is an enterprise volume management tool for Linux systems.  EXT3 is EXT2+Journaling tacked on, so that will be slow.  I don't allow storage "partitions" (or LVM logical volumes) to be larger than 4TB, regardless of the actual HDD size.  My backup storage is all standardized on 4TB storage.

For pure data, with large files, at home, where security isn't important, use NTFS if you cannot use EXT4 or ZFS.  There are specialty reasons to use other file systems, but it comes down to this summary:

**Linux Only**
[LIST]
[*]For HDDs and SSDs, EXT4 by default on Linux, unless it is purely for data, then ZFS can be used. 
[*]For flash USB/microSD/SDHC storage devices, f2fs is good when Linux file systems, permissions, are needed.
[*]LVM can be used for Volume Management, if desired for non-ZFS file systems.
[/LIST]

**Linux + Windows + Other Consumer Devices**
[LIST]
[*]For HDDs and SSDs, NTFS by default.
[*]For flash USB/microSD/SDHC storage devices, exFAT is preferred when compatible with all devices (regardless of storage size), then FAT32 for storage smaller than 64G partitions.
[/LIST]

For video storage that has to plug into other devices, use NTFS.  Avoid FAT32 as it has a 4GB file size limit. 
The lists above split the storage between HDDs/SSDs and Flash-storage devices.  Journaled file systems should always be used on HDDs/SSDs for better safety and easier recovery if something bad happens.  Journaling causes many more writes, so for write sensitive flash storage, this would drastically reduce the lifespan of the flash storage and should be avoided.

Not all file systems are equal. They each have different pros and cons.  No matter what, on 500G and larger, you really want a file system that supports journals.

**Update for clarity:**
These *rules of thumb* are for storage devices that must be directly, physically connected to different devices.  If network connectivity will be used, then stay with the Linux-only recommendations.  NFS and CIFS and SFTP and sshfs and rsync would be the primary methods to connect to storage over a network depending on security requirements and purpose.

---

### Post by sudodus on 2021-08-27
> **Lappert said:**
> So far - the first 25% happened almost immediately. Now it seems stuck on 25%, but I'm only 10 minutes into it. 

This makes me think that the drive is damaged and the process gets stuck at some sectors that are not readable or not writable. Is there S.M.A.R.T. information on the old drive? In that case test it (easy via Disks alias gnome-disks) or more detailed via smartctl (part of the program package smartmontools).

---

### Post by Lappert on 2021-08-27
Again, thank you. A lot of good information to digest.

So last night I started up KDE Partition Manager to see what would happen and left it on overnight, just to see if I got a different result than Gparted. 

It created a primary partition of 2.73 TB (and apparently it finished after 25 minutes). But here's the strange thing ... it also created a file of 44.05 GB. That might be the directory lost+found, but that directory is empty. This unknown file reduces the filespace to 2.5TB. So here's the output from KDE Partition Manager below. It says "1 large file" and 2 directories.

I'll mull this over a bit, along with all your comments. The 44GB "file" isn't making any sense,  not really, AFAIK, regular overhead and lost+found should be empty at this point. I might try it again with Gparted or Gdisk to create a NTFS partition. Your comments make sense and this particular drive is just video archives.

> 
Create a new partition (2.73 TiB, ext3) on &#8216;/dev/sdh&#8217; 

Job: Create new partition on device &#8216;/dev/sdh&#8217; 
Create new partition &#8216;/dev/sdh1&#8217;: Success

Job: Create file system &#8216;ext3&#8217; on partition &#8216;/dev/sdh1&#8217; 

Command: mkfs.ext3 -q /dev/sdh1 
Create file system &#8216;ext3&#8217; on partition &#8216;/dev/sdh1&#8217;: Success

Job: Set the file system label on partition &#8216;/dev/sdh1&#8217; to "MP4" 

Command: e2label /dev/sdh1 MP4 
Set the file system label on partition &#8216;/dev/sdh1&#8217; to "MP4": Success

Job: Check file system on partition &#8216;/dev/sdh1&#8217; 

Command: e2fsck -f -y -v /dev/sdh1 

Pass 1: Checking inodes, blocks, and sizes

Pass 2: Checking directory structure

Pass 3: Checking directory connectivity

Pass 4: Checking reference counts

Pass 5: Checking group summary information
          
11 inodes used (0.00%, out of 183148544) 
          0 non-contiguous files (0.0%) 
          0 non-contiguous directories (0.0%) 
            # of inodes with ind/dind/tind blocks: 0/0/0 
   11546855 blocks used (1.58%, out of 732566272) 
          0 bad blocks 
          1 large file
           
0 regular files 
          2 directories 
          0 character device files 
          0 block device files 
          0 fifos 
          0 links 
          0 symbolic links (0 fast symbolic links) 
          0 sockets
------------ 
          2 files 
Check file system on partition &#8216;/dev/sdh1&#8217;: Success
Create a new partition (2.73 TiB, ext3) on &#8216;/dev/sdh&#8217;: Success


---

### Post by TheFu on 2021-08-27
Please just show the output from these commands, wrapped in forum code-tags, rather than trying to describe what you think you see.

```
lsblk -e 7 -o name,size,type,fstype,label,mountpoint
df -hT -x squashfs -x tmpfs -x devtmpfs
sudo parted -l

```

Thanks.

Forum code-tags guide: [Https://ubuntuforums.org/misc.php?do=bbcode#code](Https://ubuntuforums.org/misc.php?do=bbcode#code)   I provided an example above.

**gdisk** doesn't format file systems.  It only creates partitions and partition tables.
To format a file system, **mkfs** is used.

---

### Post by Lappert on 2021-08-27
I haven't used any commands from the command line. I've only used (so far) Gparted and KDE Partition Manager. What I quoted above is the actual output of KDE Partition Manager; it's not my interpretation of what I think is happening.

Any thoughts on why I ended up with a 44GB file on the drive? The file doesn't show up anywhere, but was reported by KDE Partition Manager.

Thank you.

---

### Post by sudodus on 2021-08-27
I use command line tools or gparted for such tasks. I don't use KDE so I do not know about its partition manager. Maybe it can identify previous files or file systems and make some kind of backup. Maybe it is some kind of error because of bad sectors.

I suggest again that you try to check the S.M.A.R.T. information according to the tips in my previous post.

---

### Post by TheFu on 2021-08-27
Not sure where you got the 44G file from.  There is a difference in the way that HDD vendors count and the rest of the world.  They use 1000, not 1024, but nearly all software uses 1024b = 1KB.  Depends on which counting is used - base 10 or base 2. [https://en.wikipedia.org/wiki/Kilobyte](https://en.wikipedia.org/wiki/Kilobyte)

Also, by default, 5% of a file system is "reserved" for use by privileged processes.  For an OS partition, this is VERY important.  For 100% data partitions, I remove that reserved amount.

And lastly, formatting a partition puts markers down which use a few Kb.

For example:
```
$ sudo parted -l

Model: WD My Book 1140 (scsi)
Disk /dev/sdb: [COLOR="#FF0000"]2000GB[/COLOR]
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type      File system  Flags
 1      32.3kB  2000GB  2000GB  extended
 5      1049kB  2000GB  2000GB  logical   ext4

```
Great. But after formatting to ext4, that 2TB becomes:
```
$ df -Th | grep b5
Filesystem     Type  Size  Used Avail Use% Mounted on
/dev/sdb5      ext4  [COLOR="#FF0000"]1.8T[/COLOR]  1.4T  412G  78% /misc/2TB
```

We can see the count of inodes:
```
$ df -i
Filesystem     Inodes IUsed IFree IUse% Mounted on
/dev/sdb5        117[COLOR="#00FF00"]M[/COLOR]  320[COLOR="#FF0000"]K[/COLOR]  117M    1% /misc/2TB
```

Those reserved blocks?
```
$ sudo tune2fs -l  /dev/sdb5
...
Reserved block count:     0
...

```
File systems use something called inodes to bridge the file system -to- data locations on the disk.  When the file system is created, some number of inodes are created based on the size of the disk storage.  Running out of inodes can make for a terrible day. It is less common in disks over 10TB. Those inodes require storage, that's part of the "format".  To learn more about inodes, the wikipedia article is good enough.  [https://en.wikipedia.org/wiki/Inode](https://en.wikipedia.org/wiki/Inode)

I don't have a big HDD available to run ext3 format tests on right now. Sorry.

I think GUI tools are often too far from the hardware and over simplify what is actually happening. They often choose sub-optimal settings.  Plus, on non-desktop systems, there isn't any GUI, so I'd need to know both the GUI and non-GUI methods. Much easier to just learn 1 for me. Plus, GUIs change every few years and non-GUI tools stay about the same for 10+ yrs, if not 20+ yrs.  Anyway, that's my thought process for wanting to see CLI tools run and the output from those tools.

---

### Post by Lappert on 2021-08-28
Yes, I know about 1024. I cut my teeth on this stuff with the PDP-8, so I know at least enough to get in trouble, but not full time. And yes, I know about the OS overhead. But isn't that 5% part of the net 2.73TB? Also 44GB appears to be only about 1.4% of 3TB (if my math is correct). I don't know what it is, but I think it's something different than the OS overhead. Still, I'll look into that possibility.

Was tied up today, but hope to get back to this over the weekend. I think I might try the CLI as you suggest, and maybe the NTFS. I'll update when I have more to report. Thanks again for your assistance.

---

### Post by TheFu on 2021-08-28
Inode tables use 2MB of inodes for each 128MiB of disk.

From the mkfs.ext3 manpage:
```
              The default inode size is  controlled  by  the  mke2fs.conf(5)
              file.  In the mke2fs.conf file shipped with e2fsprogs, the de&#8208;
              fault inode size is 256 bytes for most  file  systems,  except
              for small file systems where the inode size will be 128 bytes.
```

The ext3 journal area also takes some space which is related to the total partition size.

These things can be tuned. On really large partitions, I don't bother. It is the smaller partitions where I've run out of inodes because the defaults were terribly small. Running out of inodes makes for a very bad day. Trust me.

And there are superblocks and backups of the superblocks which also take some storage. The settings, defaults, and tuning of those settings are documented in the manpages.

---

### Post by Lappert on 2021-08-28
That could very well explain it. The drive is nominally 3TB, but the net is 2.73TB. So 2.73TB / 128MB = 21,328 and multiplying that by 128MB = 42.656 GB ... which is close enough to the 44 GB being used by the unknown file.

I've never had an instance of running out of inodes (at least where I was aware of it). But I'll take your word for it. I remember in the 1980's fighting for every byte of a 64K floppy, even getting out Norton Editor to use all the space. That was MS-DOS, not Linux.

---

### Post by TheFu on 2021-08-28
> **Lappert said:**
> That could very well explain it. The drive is nominally 3TB, but the net is 2.73TB. So 2.73TB / 128MB = 21,328 and multiplying that by 128MB = 42.656 GB ... which is close enough to the 44 GB being used by the unknown file.

I've never had an instance of running out of inodes (at least where I was aware of it). But I'll take your word for it. I remember in the 1980's fighting for every byte of a 64K floppy, even getting out Norton Editor to use all the space. That was MS-DOS, not Linux.

When there aren't any inodes left on a partition, the only thing that can be done is deleting files. Nothing else. On the OS or logging partition logs cannot be created, just appended. Lots of common commands use temporary files - none of those work.  Little commands like du and df don't work.  Forget about using a GUI. They create so many temporary files as to be useless.

In the 1980s, the smallest floppies I used were 160Kb. Remember when they got DSDD floppies and 360Kb was possible.  I can probably find my old FORTRAN 66 floppies somewhere.

---

### Post by Lappert on 2021-08-28
Putting aside the PDP-8 we used in college (no floppies, programs were on paper tape), and various Wang or Xerox word processors that had 8" disks, my first computer was an Atari 800 - good machine for its time, lousy marketing. I mispoke. The Atari 810 single side single density drive (using AtariDOS) was formatted for 88 or 90K, not 64K. 

Later on, I bought a non-Atari drive (Percom), double-sided, double density floppy drive ($600) that formatted to 360K (using both sides, but you had to turn to the other side manually and use the old notch trick). That drive came with it's own OS.

---

### Post by kurt18947 on 2021-11-02
> **sudodus said:**
> This makes me think that the drive is damaged and the process gets stuck at some sectors that are not readable or not writable. Is there S.M.A.R.T. information on the old drive? In that case test it (easy via Disks alias gnome-disks) or more detailed via smartctl (part of the program package smartmontools).

That's a very good suggestion, especially for old drives.

---

