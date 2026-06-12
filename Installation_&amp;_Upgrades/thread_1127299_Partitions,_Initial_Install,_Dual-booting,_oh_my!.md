---
title: "Partitions, Initial Install, Dual-booting, oh my!"
date: 2009-04-16
forum: Installation &amp; Upgrades
---

### Post by Motlei on 2009-04-16
First the hardware involved:
- AMD Phenom X4 9850 on XFX nForce 750a Mobo
- 4GB DDR2 PC6400 (2x2GB)
- XFX 9800GTX video
- Sound Blaster X-Fi Titanium Fatal1ty Professional Series sound card (new, not installed)
- HDD1 750GB WD SATA 7200 rpm, 32MB cache
- HDD2 750GB SG SATA 7200 rpm, 16MB cache

Disclaimer: This is my first foray into dual booting any system.  I've been an USoft product user all my life, reaching even back to MS-DOS.  I'm even familiar with command-line interface.

Desired end state: Dual boot Vista x64 and Ubuntu 8.10 (likely 64bit), provide additional drive space for programs, files, swap, and file/system backup.

I am prepared to start from absolute scratch, including creating the partitions before installing operating systems on HDD1 and then erasing, reformatting, and creating partitions on HDD2 prior to writing any information to that disk.

To explain my current position on the learning curve:  From my reading over the past week, including Mark Sobell's _A Practical Guide to Ubuntu Linux_ (2009), I have concluded that for my case a well-functioning system will include Vista and the Ubuntu root directory in their separate partitions, an additional primary partition for Windows programs and then an extended partition with logical partitions for several directories for Ubuntu: /home, /usr, /tmp, etc.  This will
maximise the partition capabilities and make HDD1 the
primary hard drive used for the OS and operating programs.  The additional hard drive will then be used for Ubuntu and Vista swap partition(s), a media partition, and backup partition(s). From what I've seen it may be possible to dedicate the swap partition on the second hard drive as both Vista pagefile and Ubuntu's swap space as referenced in [URL="http://ubuntuforums.org/showthread.php?t=245393"]
this[/URL] thread.

If so, then three other partitions remain to be divided between shared music/video media, documents, and at least one partition dedicated to backups. The primary documents and files media is currently an external hard drive attached via USB.  If I cannot use the same partition on the second hard drive for swap space, then it seems wiser to create two partitions on that drive for swap space - with Vista on the outside edge of the platters and Ubuntu just inside of it.  Though the next concern then becomes whether those scratch spaces can exist comfortably inside an extended partition if necessary.

That being said, here's a partitioning plan:

Purpose of partition, Size, Filesystem
SATA HDD1:
1. Vista64 boot partition, 100GB, NTFS
2. Ubuntu 8.10 boot partition "/ [root]", 50GB, EXT3
3. Vista programs partition, 300GB, NTFS
4. Extended partition including logical drives for:
5.   Ubuntu "/home", 100GB, EXT3
6.   Ubuntu "/usr", 50GB, EXT3
7.   Ubuntu "/tmp", 50GB, EXT3
8.   Ubuntu "/var", 100GB, EXT3
SATA HDD2:
1. Media partition, 400GB, NTFS
2. Vista Backup partition, 200GB, NTFS
3. Ubuntu backup partition, 100GB, EXT3
4. Linux&Windows swap/pagefile partition, 8-16GB, swap (may not be allowed)
OR
4. Extended partition including logical drives for:
5. Vista pagefile partition, 16GB, NTFS
6. Ubuntu swap partition, 8GB, swap

Frankly, the swap partition seems to be much of the concern in this example.  It may be better to leave a primary partition on HDD2 for Windows swap file and remove the Ubuntu swap partition to a swap file on the Ubuntu extended partition though I lose the advantage of having the swap on the second drive.

Then there is the recommendations in [this]("http://ubuntuforums.org/showthread.php?p=6967615#post6967615") post.  I've adjusted the formatting and syntax to conform with my syntax above for easier comparison.  The author did not provide partition sizes or relative percentages.

HDD1
1. Windows, NTFS
2. Shared data space, NTFS
3. Linux "/boot", EXT3

HDD2
1. Debian "/" (root filesystem for Debian), EXT3
2. Ubuntu "/" (root filesystem for Ubunutu), EXT3
3. Ubuntu /swap 
4. LOGICAL PARTITION
5. Linux "/home", EXT3
6. Shared data space #2, NTFS

It appears that there's no conflict between differing filesystems in an extended partition, though I had my doubts before finding that post.

After opening and cleaning the machine this evening, I plan on installing the new HDD that becomes HDD1 in the above examples and begin partitioning.  If there is something horribly wrong with the partitioning scheme developed above, please feel free to comment.  If you have alternative suggestions that do not involve removing Vista [chuckle], please feel free to contribute.  Any other commentary regarding partition sizes, placement, filesystems, etc, is also welcome.

---

### Post by cariboo on 2009-04-16
As you are a new user, I would suggest you just use three partitions for Ubuntu, /, /home and swap. Using more than 3 partitions, just complicates things until you feel comfortable with Ubuntu. A complete install takes less than half an hour, so if you decide to change things later, it isn't to time intensive.

Jim

---

### Post by Motlei on 2009-04-16
Should I include the swap as part of the extended partition on HDD1 or continue to monkey with the idea of leaving the swap partition on HDD2 as part of an extended partition shared with the NTFS logical partition for Vista's pagefile?

---

