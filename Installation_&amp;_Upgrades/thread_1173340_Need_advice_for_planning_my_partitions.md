---
title: "Need advice for planning my partitions"
date: 2009-05-29
forum: Installation &amp; Upgrades
---

### Post by brncao on 2009-05-29
Hi folks. I'm new to Linux. Ubuntu will be my first distro.

I wanted to dual boot Windows 7 RC and Ubuntu. I need some suggestions on what partitions I would need and how much space should each get. I have 200gb hdd (will add 160gb as well, which is 360gb total) and 2gb of RAM.

This is what I was thinking.

1. Windows 7
2. Ubuntu (ext3) /home - shared data
3. Ubuntu (ext3) /
4. Recovery and backups of #2 duplicated to another separate hdd partition
5. Swap

I don't know what's "primary" and "logical." From what I've read you can only have up to 4 primaries. I would like to have the /home directory accessed (read/write) by both OS. How would I do this? I would like to have Ubuntu write/read in NTFS in /home so it can be accessed by Windows.

To get an idea with what I do (so you can determine the right size for me), I work with DAW, music, and audio applications and usually have wads of plugins and vst's. I install a bunch of classic to modern games as well. These installations eat up the most space.

I download lots of music, videos, and downloaded programs (they go in the /home directory).

So what are your recommendations?

---

### Post by lake54 on 2009-05-29
I'm new to Linux as well, but essentially if you were going to use Windows and Ubuntu equally, I'd create 'equal' partitions (i.e. Windows 100 gig, Ubuntu 100 gig, which gets split down).

Alternatively, if I was going to use Linux more, 50 gig for Windows, and 150 for Linux, and vice versa.

I wouldn't worry too much about a few gigs here or there.

As a final suggestion, in relation to the home dir, you could have 50 for each OS (50 gigs for Windows, 50 for Linux) then keep your home directory as 100.

Hope that helped somewhat.

James

---

### Post by logos34 on 2009-05-29
> **brncao said:**
> I don't know what's "primary" and "logical." From what I've read you can only have up to 4 primaries. I would like to have the /home directory accessed (read/write) by both OS. How would I do this? I would like to have Ubuntu write/read in NTFS in /home so it can be accessed by Windows.

I think the best way to do it is install windows, then use gparted on the ubuntu live cd desktop (system>admin>partition editor) to create a new extended partition out of all the remaining space.  Install ubuntu inside that.  (logical partitions are what they are called when inside and extended.   Max. 63 logical partitions).  An extended is simply a special type of primary partitions which allows you to circumvent the 4 partition limit.

Just make sure to use the default ext3 filesystem when you install 9.04.  Ext4 is not yet supported by [fs-driver]("http://www.fs-driver.org/"), so you wouldn't be able access your files from wind7.

---

### Post by anarchyinc on 2009-05-29
You can go a few ways with this, here is my idea;
 
/windows (NTFS)= size of the installed OS plus about 5 gigs or so space for new programs and viruses
/root (ext3)= 5 to 10 gigs (plenty of room, trust me)
/home (ext3)= 5 to 10 gigs also
/share (ext3 or FAT32)= everything else.
 
Windows can read ext3 format with little effort once the proper programs are up and running. I would put the shared drive by itself just in case windows messes it up somehow so as to preserve your /home. You could also make the share FAT32 but then you will have more of a headache correcting issues with FAT32 from a linux environment than the other way around. It is however easier to setup. If you are a big torrent user you will see why not to format to FAT32 pretty quick.

---

### Post by coffeecat on 2009-05-29
> **brncao said:**
> 2. Ubuntu (ext3) /home - shared data

If you were thinking of sharing the data with Windows 7, I'm afraid that won't work - at least not easily. Windows 7 can't read or write the ext3 filesystem. There are 3rd party ext3 drivers for Windows out there, but I don't know if any of them will work with W7. Personally, I wouldn't use a Windows ext2/3 driver – they're never 100% reliable and could damage the filesystem - but instead I prefer a separate data partition.

How about this? Keep /home in your / partition, but create a NTFS shared data partition. This would become E:\ (or whatever) in W7 and, so long as you set up the data partition to be mounted on bootup, you could create symlinks from the data partition folders to your /home folder.

This works well for me on a Vista/Ubuntu machine and on a Windows 7/Ubuntu machine. Ubuntu Jaunty reads and writes NTFS reliably, I haven't had a filesystem corruption with internal NTFS partitions and, even if I did, I have Windows there to repair the NTFS partition if need be.

By the way, you may want to avoid writing to the W7 partition from Ubuntu. Some people have had problems with Vista after writing to the C: partition from Ubuntu. Windows 7 may react as badly.

I agree with **logos34** to put all your Ubuntu partitions in logical partitions in an extended. What you could do is:

Partition 1 - primary - NTFS - Windows 7
Partition 2 - primary - NTFS - Shared Data
Partition 3 - Extended for Ubuntu partitions (/ and swap) + whatever backup partitions you want.

---

### Post by logos34 on 2009-05-29
> **coffeecat said:**
> If you were thinking of sharing the data with Windows 7, I'm afraid that won't work - at least not easily. Windows 7 can't read or write the ext3 filesystem. There are 3rd party ext3 drivers for Windows out there, but I don't know if any of them will work with W7. Personally, I wouldn't use a Windows ext2/3 driver – they're never 100% reliable and could damage the filesystem - but instead I prefer a separate data partition.

There was apparently an issue with windows 7 beta forgetting the assigned drive letters on reboot, but I thought it was resolved.  Says:

> Supports Windows NT 4.0, Windows 2000, Windows XP, Windows 2003, Windows Vista and Windows 2008.

but then again maybe they're referring to windows *server* 2008

> Keep /home in your / partition, but create a NTFS shared data partition.

That's how mine used to be set up, back when I was still dual booting

---

### Post by brncao on 2009-05-29
> **coffeecat said:**
> so long as you set up the data partition to be mounted on bootup, you could create symlinks from the data partition folders to your /home folder.

Can you explain to me how? I haven't installed Linux yet.

What's a good method to duplicate partition 2 on another hard drive? I've heard of RAID 1, but I've never done RAIDs before. What do I need to know?

---

### Post by coffeecat on 2009-05-29
> **brncao said:**
> Can you explain to me how? I haven't installed Linux yet.

If you go for the manual option at the partitioning stage, you can specify a mountpoint for the NTFS data partition - say /media/data - and the installer will handle writing a line to /etc/fstab for this.

Alternatively, just let the installer do its thing because you'll still be able to mount the data partition from the Places menu after bootup. You could then post again if you need help for adding a line to /etc/fstab.

For the record, there's a small bug in the fstab line that the Ubuntu installer uses. This is the line that the installer set up on one of my systems:

```
UUID=48EA808EEA807A48 /media/Data     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
```Which works well enough until you copy a file (by GUI drag and drop) from an ext3 partition to the mounted NTFS partition, upon which the time/date stamp gets changed to current. Which is bad. Strangely, not the other way round though - timestamp is preserved. I get round this by changing the line to the simpler:

```
UUID=48EA808EEA807A48 /media/Data     ntfs    defaults    0       1
```... and everything works fine. If you're new to Linux, this may not mean much to you now, but I've posted this so that you can refer to it later if need be.

---

### Post by logos34 on 2009-05-29
> **brncao said:**
> What's a good method to duplicate partition 2 on another hard drive?

why not just do incremental backups with Rsync or Simple Backup Program (or a windows app)?

---

### Post by brncao on 2009-06-02
Thanks! I'll try out Rsync or Simple Backup Program. Another question, can I install programs on a single partition that holds all the installed applications that can be accessed by several OS? I don't want to reinstall them again when I reformat the OS.

---

### Post by logos34 on 2009-06-02
> **brncao said:**
> Thanks! I'll try out Rsync or Simple Backup Program. Another question, can I install programs on a single partition that holds all the installed applications that can be accessed by several OS? I don't want to reinstall them again when I reformat the OS.

no, you can share /home or data partitions, but not / with all the programs.  (different OS's have different pkgs).

You can back up all your installed apps by using a tool like AptOnCD.  Or simply backup all the .debs in /var/cache/apt/archives.  Then make a list of all your apps:

> dpkg --get-selections > my_applications

To restore them, copy the backup .debs to their original location and run this:
> 
dpkg --**s**et-selections **<** my_applications

---

### Post by Xavier71 on 2009-06-04
Having read this thread this is as close to my question as I can find, but not quite :-)

I have a 250Gb hard drive currently partitioned as follow:

- 10Gb EISA for recovery (Samsung laptop)
- 185Gb NTFS for Windows Vista
- 36Gb for Ubuntu 9.04 
- 2Gb for the swap

Both system happily dual-boot but I've come to realise that I made a mistake in that I cannot read/write/modify my Windows files from Ubuntu with this partition system so I wonder how I can do best to create a 5th partition that would contain all my data files (pictures, music, ...) so that I can access them from Windows AND Ubuntu and do whatever I want with them from both systems.  

I am currently in the process of shrinking the Vista partition and the plan is to leave about 80Gb for Vista.  My main question is : once I have shrunk the drive, which format should I use to make the new partition visible from both Vista and Ubuntu (i.e. which format to use?).  And if I do that from Windows - that would make sense as I already use shrink - how do I get Ubuntu to see this new partition?  And finally, is there any pitfall I should be careful about?

---

### Post by coffeecat on 2009-06-04
> **Xavier71 said:**
> I cannot read/write/modify my Windows files from Ubuntu with this partition system

You should be able to. Ubuntu can read/write NTFS filesystems quite reliably and your Vista partition should be mountable from somewhere within the Places menu. I have no problems reading/writing NTFS partitions from Ubuntu. However, you might want to avoid writing to a Vista C: partition from Ubuntu. XP never seemed to mind but some people have had problems with Vista after a Linux write to the filesystem.

> **Xavier71 said:**
> which format should I use to make the new partition visible from both Vista and Ubuntu

I use NTFS for exactly this same purpose. In fact my Vista/Ubuntu layout on my laptop is very similar to what yours is going to be. You can get ext2/3 drivers for Vista, but Linux NTFS drivers are probably better than Windows ext2/3 drivers. Once you've created the NTFS partition, you should be able to access it from the Places menu again. And if you want the new partition mounted on bootup, post the terminal output of:

```
sudo fdisk -l
```

... and someone can suggest a line to put into /etc/fstab

---

### Post by naugiedoggie on 2009-06-04
> **brncao said:**
> Hi folks. I'm new to Linux. Ubuntu will be my first distro.

I wanted to dual boot Windows 7 RC and Ubuntu. I need some suggestions on what partitions I would need and how much space should each get. I have 200gb hdd (will add 160gb as well, which is 360gb total) and 2gb of RAM.

This is what I was thinking.

1. Windows 7
2. Ubuntu (ext3) /home - shared data
3. Ubuntu (ext3) /
4. Recovery and backups of #2 duplicated to another separate hdd partition
5. Swap

I don't know what's "primary" and "logical." From what I've read you can only have up to 4 primaries. I would like to have the /home directory accessed (read/write) by both OS. How would I do this? I would like to have Ubuntu write/read in NTFS in /home so it can be accessed by Windows.

To get an idea with what I do (so you can determine the right size for me), I work with DAW, music, and audio applications and usually have wads of plugins and vst's. I install a bunch of classic to modern games as well. These installations eat up the most space.

I download lots of music, videos, and downloaded programs (they go in the /home directory).

So what are your recommendations?

Hello,

VMWare.  That's the short answer -- don't mess with dual boot, if you use a virtual machine you can have both running at once.  Of course, that's not recommended unless you have a dual proc or dual core system with at least 4 GB RAM.  But you can start/stop a VM in about 30 seconds, as opposed to having to reboot every time you want to switch OS.  If you actually use both systems, you may quickly become annoyed at having to reboot every time you need a file or to look up something that's on the other partition.  I did.

The longer answer is, I don't believe there is any legitimate reason to fiddle with multiple partitions with a packaged desktop  system like Ubuntu.  The only real point to having a /home partition would be if it was NFS and shared across a network or you are using multiple disks and putting partitions on their own disks (which is common practice in Unix).  These days, and especially in the configuration you are targeting, it's all just disk space.

Also, I fail to see a point in "backing up" data to the same drive.  The principal reason for a backup is to guard against disk failure!  All you're doing is storing the data, that's not the same as a backup!  You might want to look at R-Drive Image, which is a relatively inexpensive tool that images drives.  It runs on Windows but it images at the byte level, so it doesn't care what's on the disk.  You can get a 300 GB USB drive for about $100, buy one and have R-Drive update the image nightly.  The nice thing about imaging is a 'restore' consists of imaging the new drive and rebooting.

Thanks.

mp

---

### Post by meka4996 on 2009-10-25
[http://ubuntuforums.org/showthread.php?t=1300461](http://ubuntuforums.org/showthread.php?t=1300461)
Partition Table Design Scheme for Multi Boot Many/Multiple Linux Distro, Windows OS, or Mac, using Grub bootloader

---

