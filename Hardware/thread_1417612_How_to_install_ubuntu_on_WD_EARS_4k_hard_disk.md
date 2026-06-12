---
title: "How to install ubuntu on WD EARS 4k hard disk"
date: 2010-02-27
forum: Hardware
---

### Post by mgiammarco on 2010-02-27
Hello,

as you can see on this url: [http://www.osnews.com/story/22872/Linux_Not_Fully_Prepared_for_4096-Byte_Sector_Hard_Drives]("http://www.osnews.com/story/22872/Linux_Not_Fully_Prepared_for_4096-Byte_Sector_Hard_Drives")

Linux may have problems with WD hard disks with 4k sectors.

I would like to install Ubuntu now on a 4k sectors hdd.
How can I do it? 

Thanks in advance for interest!

Mario

---

### Post by mgiammarco on 2010-03-01
I have searched in forums and it seems that all people recognize the problem but no one give a solution.

Some people say: "the last version of parted or fdisk uses right parameters, so compile it and use it". 

Sure, but I am installing ubuntu 9.10, I cannot compile fdisk before installing ubuntu.

With current ubuntu installer what can I do?

Thanks!

---

### Post by Objekt on 2010-03-01
Yeah, someone telling you "download the source and compile latest version of xxx" is a pretty much unacceptable answer, especially for someone new to Ubuntu.  I have been using various kinds of Linux for almost a year, but I still don't have a clue how to compile from source.

I'm not sure I understand your problem.  Are you able to install Ubuntu 9.10 on the Advanced Format drive?  Or did you try yet?  

What I've been reading is that you CAN install some operating systems (such as Ubuntu 9.10) on the Advanced Format drives, but the performance is really terrible because they don't deal with the Advanced Format correctly.  Western Digital offers a utility called "WD Align" to fix the problems, but it's only for Windows XP/Vista/7.

Of course that doesn't help you, but it's all I got for now. :P

---

### Post by mgiammarco on 2010-03-03
I can install ubuntu on wd ears hard disk easily and it works.

But the problem is:

1) The partitions made by ubuntu are aligned or not? If they are not aligned I lose 2/3 of writing speed.
2) How can I easy test that I have lost that speed? The wd ears is a new model and it is very fast, faster than my old hdd. I have done some test with bonnie++ without luck.
3) If I discover that ubuntu 9.10 installation cd partitions it in a bad way where can I find a live cd with updated parted or fdisk? (or another way to do it).

I think that it is a big problem because in the future all hard disk will have 4k sectors.

---

### Post by SeePU on 2010-03-07
I've sent some links of the problem.   Some describe it and some include examples.   Some are better written than others.

I still am confused as there's so many variables and I'm not used to manually creating partitions.   I usually use gparted (the gui) and leave the defaults.   But, you can't do that with these drives in Linux yet.   Not until the gparted/parted developers alter gparted and how it currently works to support these drives.

I think you have to choose a different starting sector than 63.   It has to be divisable by 8.  You can use fdisk to do this or parted.   I don't know what the starting sector should be.   Some reviwers have chosen 32, 40, 48, 56 and 64.   I don't know why there isn't an ideal or 'favored' method or number but that is what is confusing.   Some people say you should change the number of heads from 255 to something else as well.   224 has been chosen in some examples.   But, why that number?

Anyway, check out the links and see what you think.

---

### Post by mgiammarco on 2010-03-08
Thanks for the links. Infact I have read some of them.
I have discovered one big problem infact: I partitioned the disk with fdisk putting first sector 64 then 63. Compared results and they were similar. Then I used 224 heads as parameter to fdisk and I discovered that even the partition that I supposed that was starting at 64 now starts at 63.

So I am very confused.

Thanks for help!

---

### Post by SeePU on 2010-03-08
Some of those articles talks about how the hardware 'lies' to the partition programs.  If you try 'fdisk -l', it should show what sector it starts at?  It should be a multiple of 8.  If it shows 64, that should be okay.  

If I had one of those drives and wanted to use a partition program in Linux (for e.g. GParted, System Rescue CD, Parted Magic, QtParted etc. etc.), I would read up on the various options in parted and fdisk.  I think you might want to manually set the partition options and then use some commands to align the partitions.  I would do this and run the commands in the examples of those articles to CHECK whether it's really aligned or not.  

I think WD just figured they want to release these drives without really caring whether you have to do anything in Linux or they REALLY REALLY underestimated what happens when you partition these in Linux.  Translation:  they WEREN'T tested in Linux, only Windows.

There are drive/disk experts in those articles but I wish there were more detailed examples instead of just discussing the problems.  Also, much of it applies specifically to SSD drives but what about Advanced Format drives, right?

Also, try 'fdisk -l -u' and/or try the command for changing the unit to sectors.  The starting and end sectors should be multiples of eight so if it still shows starting at 63, it's probably not aligned.

---

### Post by mgiammarco on 2010-03-08
> **SeePU said:**
> Some of those articles talks about how the hardware 'lies' to the partition programs.  If you try 'fdisk -l', it should show what sector it starts at?  It should be a multiple of 8.  If it shows 64, that should be okay.  

Also, try 'fdisk -l -u' and/or try the command for changing the unit to sectors.  The starting and end sectors should be multiples of eight so if it still shows starting at 63, it's probably not aligned.

Infact the problem is this! I set with fdisk the start of a partition as a multiple of 8. Then I change unit or number of heads, I check again the partition and I discover it starts from 63 (head? sectors? whatelse??)

I am VERY confused...

---

### Post by SeePU on 2010-03-08
> **mgiammarco said:**
> Infact the problem is this! I set with fdisk the start of a partition as a multiple of 8. Then I change unit or number of heads, I check again the partition and I discover it starts from 63 (head? sectors? whatelse??)

I am VERY confused...
Can you post the output of 'fdisk -l -u' and if possible, what commands you used to set what the starting sector to be?   Basically, post what you did if it's not too much trouble?

I'm curious and maybe I can spot something.  

I am considring one of these drives and would like to know what to do already.

---

### Post by Fafler on 2010-03-09
A way of making sure everything is done the right way when installing to a EARS drive, is to download the alternate boot CD. When you get to the "partition drive" menu, press alt-f2, enter and use fdisk from the terminal. Type x in fdisk to enter expert mode, like someone else mentioned earlier, setup the partitions according to the guidelines in this thread (start every partition on a sector which is a power of 8), write the changes, press alt-f1, select manual, and just specify mount points for your new partitions. 

I don't really have time to test how the installer works with this kind of drives, but while i was fiddling around with a RAID 5 setup on three of these yesterday, i noticed some weird performance changes from time to time, seemingly dependent on the version of fdisk being used. But i'm not sure about this, because it wasn't really what i was looking for. Now i will definitely look into this and make sure the partitions are made the right way.

---

### Post by SeePU on 2010-03-09
> use fdisk from the terminal. Type x in fdisk to enter expert mode, like someone else mentioned earlier, setup the partitions according to the guidelines in this thread (start every partition on a sector which is a power of *8*, write the changes, press alt-f1, select manual, and just specify mount points for your new partitions. I think using fdisk and using expert mode is the way to go.  I am not familiar with expert mode, though, so I ought to familiarize myself with it if I get one of these drives.

I don't recommend installing an OS on it though. Even if you successfully align partitions to 4Kb sectors, it is still too slow for an OS drive.  It's a storage drive with 5400rpm speed.  But, I am reading that if you can align the partitions properly, it's great for storage (low heat/power and good performance for a slow drive).  If you don't align the partitions properly and use a standard partition format, it will be really slow at writing.  Read speeds might not be bad but writing will be abysmally slow.

---

### Post by cascade9 on 2010-03-09
> **SeePU said:**
> I don't recommend installing an OS on it though. Even if you successfully align partitions to 4Kb sectors, it is still too slow for an OS drive.  It's a storage drive with 5400rpm speed.  But, I am reading that if you can align the partitions properly, it's great for storage (low heat/power and good performance for a slow drive).  If you don't align the partitions properly and use a standard partition format, it will be really slow at writing.  Read speeds might not be bad but writing will be abysmally slow.

It might be 5400, but seriously...its faster than you might guess.. I changed from a 80GB Seagate SATA (7200.8 IIRC, cant be bothered to pull the side of my case right now to check) to a EADS 1TB drive, and the speed was noticably faster.  A modern 5400 will run rings around older 7200s.

Its not like there is a massive difference in perfromance between the modern 7200s and the 5400s. Writing 'abysmally slow'? Hardly. I'd like to see a source for that...or else its FUD. Depending on the test a EADS can best some of the 7200 drives (and yes, I do have sources..this is just one of many)- 

[http://www.xbitlabs.com/articles/storage/display/1tb-hdd-roundup-3.html](http://www.xbitlabs.com/articles/storage/display/1tb-hdd-roundup-3.html)

The EARS still has some issues, but I'm hoping that newer firmware and a bit more work from WD will bring them 'up to speed' LOL

*Edit- I'd still be avoiding the EARS for the time being, it seem from that test that it is slower than the EADS drives.

---

### Post by SeePU on 2010-03-12
> **cascade9 said:**
> The EARS still has some issues, but I'm hoping that newer firmware and a bit more work from WD will bring them 'up to speed' LOL

*Edit- I'd still be avoiding the EARS for the time being, it seem from that test that it is slower than the EADS drives.
There are conflicting reviews and tests and I'm not sure what to think.   That link you posted shows the EARS as underperforming especially on writes even when aligned.  But, this:

[http://hothardware.com/Articles/WDs-1TB-Caviar-Green-w-Advanced-Format-Windows-XP-Users-Pay-Attention/?page=2](http://hothardware.com/Articles/WDs-1TB-Caviar-Green-w-Advanced-Format-Windows-XP-Users-Pay-Attention/?page=2)

---

### Post by srs5694 on 2010-03-12
I'd use [PartedMagic[, [url=http://www.sysresccd.org/Main_Page]System Rescue Cd,](, [url=http://www.sysresccd.org/Main_Page]System Rescue Cd,) or some other Linux emergency disc to set up the drive prior to installing an OS. Use whatever tricks your favorite partitioning software supports to set the sectors up on 4K boundaries. It can be done with either fdisk or GNU Parted. FWIW, I've updated my own [url=http://www.rodsbooks.com/gdisk/]GPT fdisk](http://partedmagic.com/) partitioning software, which edits GPT partition definitions, to do this by default on larger drives, but you need version 0.5.2, 0.6.0, or later to do it. (I tried detecting the drive type in 0.5.3, but that failed, so this version doesn't do the alignment unless you tell it to using an option on the experts' menu.) GPT fdisk comes with both PartedMagic and System Rescue Cd, but I don't happen to know what versions come with the latest versions of these discs. Since GPT fdisk reports and accepts partition start points in terms of sectors, you can easily align them properly even in older versions just by ensuring the sectors start at values that are divisible by 8. Starting the first partition at sector 40 and then using partition sizes that are multiples of 4K should keep everything aligned after that point.

FWIW, in my own benchmarks, a 1TiB Caviar Green drive with Advanced Format technology sees only modest performance degradation on misaligned partitions for read operations and write operations involving large files. When writing many small files, as in extracting a Linux kernel source tarball, the performance hit is in the 10x-30x range with most filesystems, although newer ones (ext4fs, Brtrfs) fare better. By "performance hit... in the 10x-30x range," I mean that an operation that takes 1 minute on a properly-aligned partition takes 10-30 minutes on a misaligned partition. So this is a reason for *very* careful attention to detail when you set up the partitions!

---

### Post by CarloMagno on 2010-03-15
I've been following the discussion in this thread because I have set up recently a new system based on Intel i3 processor, H55 chipset motherboard and WD150EARS HDD. Since the main use of this system is an "always on" Mythtv box, media server and web server I wanted it to use the minimum amount of energy while in stand-by. There are 2 more green WD in the system (1,5 TB EADS and 1 TB EACS).
I know it is not recommended to install OS in this type of drive but as the other two drives have ability to park while in idle, I decided to set 5 partition on the new EARS:
 - sda1 for W7 in case I want to install it in future
 - sda2 with Karmic as main OS
 - sda3 with Lucid as testing OS
 - sda4 extended:
    - sda5 swap
    - sda6 data
In data I will store media that is accessed frequently as working documents, samba server shares, music, recordings from MythTV and pictures. The other drives sdb and sdc will contain video files that I don't access frequently such as old TV series, ripped DVDs and documentaries that I want to keep.

This way, although I would not get a great performance having a single drive for OS and media, most of the time sdb and sdc would be in idle state requiring only 1-3W and sda would be constantly in use.

After setting up Karmic I have found this and other threads regarding the alignment issues with these drives:

[http://community.wdc.com/t5/Desktop/WDC-WD15EARS-00Z5B1-awful-performance/m-p/5242]("http://community.wdc.com/t5/Desktop/WDC-WD15EARS-00Z5B1-awful-performance/m-p/5242")

[http://ubuntuforums.org/showthread.php?t=1407098&page=1]("http://ubuntuforums.org/showthread.php?t=1407098&page=1")

I tested my partition table with "fdisk -l -u" and I have seen that my first partition starts in 63 (instead of suggested 64). So I would like to know your opinion regarding what to do:

a) Since the system is already up and running, do nothing and live with the performance hit

b) Re-install everything from scratch (delete all partitions and create new partitions)

c) Move and resize partitions to align them properly

d) Buy a new faster/noisier/warmer drive and install there the OS and frequently accessed data because performance is way better and as the drive will be working most of the time the energy saving will be minimal.

For b) is there a way to copy the existing installation in Karmic and pasting it in a new partition?. I was thinking in copying the full partition with clonezilla to an external drive, deleting OS partitions, creating new partitions starting and ending at multiples of 8k, and restoring the back-up partition to the newly created partition
Is c) feasible?, I don't even know if is possible to move a partition without destroying the data or confuse grub.

---

### Post by srs5694 on 2010-03-15
> **CarloMagno said:**
> I tested my partition table with "fdisk -l -u" and I have seen that my first partition starts in 63 (instead of suggested 64). So I would like to know your opinion regarding what to do:

First, check the start point of *every* partition, not just the first one. If you're very lucky you'll only have to adjust one partition, rather than all of them.

> a) Since the system is already up and running, do nothing and live with the performance hit

b) Re-install everything from scratch (delete all partitions and create new partitions)

c) Move and resize partitions to align them properly

d) Buy a new faster/noisier/warmer drive and install there the OS and frequently accessed data because performance is way better and as the drive will be working most of the time the energy saving will be minimal.

Personally, I'd try option C. WD has a utility on their Web site to perform the alignment, but it only runs under Windows. I don't know if it handles Linux filesystems. If it does, you could move the disk to a Windows box to perform the alignment. If not, you'll have to try using GNU Parted, GParted, or a similar utility in Linux. I'm not sure how easy this will be; these utilities like to work in larger units and may try to round to their preferred units or to cylinder boundaries, which are unlikely to match the 8-sector boundaries required of your drive. Not having tried it, I'd speculate that you're more likely to coax the text-mode GNU Parted into aligning the partitions than the GUI GParted, but that's just speculation on my part.

Failing that, I'd back up everything, repartition, and restore; however, that is a bit of a hassle, and you're most likely to see performance problems when writing many small files (uncompressing a Linux kernel source archive or installing a package that contains many small files, for instance). If you don't expect to do such things very often, the path of least resistance might be to live with the problems.

> For b) is there a way to copy the existing installation in Karmic and pasting it in a new partition?. I was thinking in copying the full partition with clonezilla to an external drive, deleting OS partitions, creating new partitions starting and ending at multiples of 8k, and restoring the back-up partition to the newly created partition

Yes, this should work. If you can clear space on the current drive, there may be a simpler way. Suppose you don't need your data partition (/dev/sda6), or can shrink it to be small enough to create a new Karmic partition after it. You can create that partition (properly aligned) create a filesystem on it, and copy your existing setup using tar. For instance, if you mount the new system at /mnt, you could copy the system thus:

```

cd /
sudo tar cpf - --one-file-system ./ | (cd /mnt; sudo tar xvpf -)

```

Be careful with the dashes, spaces, and other symbols in this command; a typo can produce results you don't want. When the copy finishes, adjust /mnt/etc/fstab and your boot loader and reboot to test the new system. Depending on your boot loader configuration, you may then need to re-install it to use the boot loader files (/boot/grub/menu.lst, etc.) on the copied installation. Once you're satisfied it's working, you can delete the original Karmic installation on /dev/sda2 and convert another partition in a similar way.

This is a somewhat delicate dance. It's not difficult once you understand it, but if you slip up and don't understand your system very well it can be frustrating to get back on the right track.

---

### Post by CarloMagno on 2010-03-16
srs5694, Thank you for your quick answer.

I will follow your advice and will try to move the partitions first. I have seen that the latest live cd from gparted project already support moving and resizing ext4 partitions:
[http://gparted.sourceforge.net/features.php#blkid]("http://gparted.sourceforge.net/features.php#blkid")

The steps I am planning to follow are:
0a) backup partition sda2 (karmic) with clonezilla live CD (just in case of disaster)
0b) detach sdb and sdc to avoid mistakes

1) boot with gparted live CD 
2) Move and resize sda3 (Lucid testing partition)
3) Edit fstab in sda3 to reflect changes in UUID of sda3 partition
4) boot in sda3 and check if everything has been all right
5) In case of success I will do the same for sda2 (Karmic), move sda1 (not used for windows yet)and move sda5 (swap) and sda6(ext3 data).

In case It doesn't work I will follow your second option:
1) boot with gparted live CD
2) Delete sda1 (blank for future win7) and sda3 (lucid testing partition)
3) Create new sda1 (no filesystem) and sda3 (ext4) partitions correctly aligned
4) Boot in sda2 (karmic), mount sda3 in /mnt and copy filesystem to sda3 with your suggested command: ```
sudo tar cpf - --one-file-system ./ | (cd /mnt; sudo tar xvpf -)
```
5) edit /mnt/etc/fstab in sda3 to set the UUID of the new partition
6) reconfigure grub2: "sudo update-grub" so that changes are reflected in boot menu.
7) try to boot from new sda3 (karmic correctly aligned) and if it works:
8) delete sda2 and create a new sda2 correctly aligned
9) copy filesystem in sda3 to new sda2 and update grub2 menu again.

Now all I have to do is try to find a 3hr window for downtime of the system (have to check availability with wife :-) ). I will post my results here once done (tentative 1 week time).

Thanks again for your time and suggestions

---

### Post by BMWolf on 2010-04-12
I have a question that is similar to this and maybe not worth it's own thread. 

I had the main disc die on my file/LAMP testing server and decided that while I was putting some time into getting a server up and running again, I'd just build a new more powerful and energy efficient system to replace it all together. :) The new server runs a Caviar blue as the system disc, so no problem there. However, I've ordered two of these WD EARS drives to run in a software RAID1 for data. This will be purely a data drive with one big partition to hold /home and a samba share. 

**Question 1:** Do I need to do anything special when formatting and building the array if it is only going to be one big data partition?

**Question 2:** Are there any longevity concerns with the drives spinning down when not in use? Should I find a way to make them not spin down? If yes, any clue how to do this? 

Thanks in advance!

BTW, I'm running Server 9.10 64-bit if it matters.

---

### Post by srs5694 on 2010-04-12
> **BMWolf said:**
> I've ordered two of these WD EARS drives to run in a software RAID1 for data. This will be purely a data drive with one big partition to hold /home and a samba share. 

**Question 1:** Do I need to do anything special when formatting and building the array if it is only going to be one big data partition?

You've got the same issues whether you use the disk as a conventional filesystem-on-a-partition configuration, an LVM setup, or a RAID setup. Align your partitions on 4096-byte (8-sector) boundaries or risk poor performance. The degree of degradation varies from one filesystem to another and from one type of operation to another, but with foreknowledge of the problem, you shouldn't try to second-guess the filesystem -- just align the partitions properly.

**> Question 2:** Are there any longevity concerns with the drives spinning down when not in use? Should I find a way to make them not spin down? If yes, any clue how to do this?

I doubt if there's anything special about these new drives in this respect. The question you're asking is one that's been hotly debated for many years. Some people say that the action of spinning drives up and down is inherently more destructive than letting them run for the intervening period, while others disagree. Beyond that, I'm going to duck and stay out of this debate.

---

### Post by BMWolf on 2010-04-13
> **srs5694 said:**
> You've got the same issues whether you use the disk as a conventional filesystem-on-a-partition configuration, an LVM setup, or a RAID setup. Align your partitions on 4096-byte (8-sector) boundaries or risk poor performance...

Thanks! Will do.


> **srs5694 said:**
> I doubt if there's anything special about these new drives in this respect. The question you're asking is one that's been hotly debated for many years. Some people say that the action of spinning drives up and down is inherently more destructive than letting them run for the intervening period, while others disagree. Beyond that, I'm going to duck and stay out of this debate.

I've heard that these drives spin back up pretty slowly. Being a personal file server they will be idle many times throughout the day. Whether the constant spinning up & down  would be more problematic with these drives is unknown, I doubt it, but I wondered what others thought before it was too late to return them. Thanks for chiming in!

I've also read a few bad reviews on amazon that led to some searching, which led me to this forum post, particularly post #11: [RAID issues...]("http://www.tomshardware.com/forum/251076-32-raid-issues-western-digital-hard-disk") and an [Amazon review that concerned me]("http://www.amazon.com/review/R2GLN3MSLNW72L/ref=cm_cr_rdp_perm")

Seems their error checking can take a long time causing them to get kicked from the array. I imagine many desktop drives behave this way, what I wonder though, is how spin up time could or could not make this more problematic?

I'll just give them a go and see what happens. That said, I'd still be interested in ways to control when they are allowed to spin all the way down; only between the hours of 2-7am, for example. Anyone know how to do that?

Thanks for the help!

---

### Post by BMWolf on 2010-04-14
New day, new info. The drives are up and working just fine in my raid 1 setup, but I did come across something that might be of interest for owners of the WD green drives; not just the EARS, but also the EADS.

[http://forums.overclockers.com.au/showthread.php?p=11628963](http://forums.overclockers.com.au/showthread.php?p=11628963)

and 

[http://forums.whirlpool.net.au/forum-replies-archive.cfm/1367904.html](http://forums.whirlpool.net.au/forum-replies-archive.cfm/1367904.html)

Seems that when used in Linux, excessive use of the Intellipark(head parking) can *potentially* cause the drives to fail prematurely. Maybe or maybe not a concern.

**EDIT: I've been monitoring my drives with smartctl and it seems that the head parking is not an issue on my setup. It's probably only a concern if it's used as a system disk or if the data is accessed heavily.**

This is the command I've been using to check them:
```
date; sudo smartctl -a /dev/sda | grep -i -E '(load_cycle|temp|Start|Spin_UP|Power_On|Power_Cycle)'
```

...and the output:
```
Thu Apr 15 11:28:54 CDT 2010
=== START OF INFORMATION SECTION ===
=== START OF READ SMART DATA SECTION ===
  3 Spin_Up_Time            0x0027   129   129   021    Pre-fail  Always       -       6525
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       11
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       14
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       9
193 Load_Cycle_Count        0x0032   200   200   000    Old_age   Always       -       71
194 Temperature_Celsius     0x0022   120   115   000    Old_age   Always       -       27

```

Should I be worried that the 'Spin_Up_Time' is so high for only 14hours of 'Power_on'?

---

### Post by bruceschaller on 2010-05-17
Hey all,

I found this topic rather frustrating, so I made a calculator in openoffice which shows the starting and ending sectors for an aligned drive. 

To use it, the desired size of the partition in whole gigabytes is entered, and starting and ending sectors are calculated.


Here's the link

[http://dl.dropbox.com/u/3235562/Advaced_Format_Calculator.ods]("http://dl.dropbox.com/u/3235562/Advaced_Format_Calculator.ods")

I hope that it is useful!

Bruce S

---

### Post by ZanexGt on 2010-05-24
What do you guys think, according to below, are my partitions aligned properly? 

I was shooting for a 4GB partition to use as swap space and the second partition to take up the rest of the free space on the drive. Neither partition has been formatted yet.

```
Command (m for help): p

Disk /dev/sdc: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00036915

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              64     8388672     4194304+  83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sdc2         8388673  3907029167  1949320247+  83  Linux

Command (m for help): 

```

---

### Post by srs5694 on 2010-05-25
> **ZanexGt said:**
> What do you guys think, according to below, are my partitions aligned properly? 

```
Command (m for help): p

Disk /dev/sdc: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00036915

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              64     8388672     4194304+  83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sdc2         8388673  3907029167  1949320247+  83  Linux

Command (m for help): 

```

No. A properly aligned partition begins on a sector that's a multiple of 8. /dev/sdc2 begins on an odd-numbered sector, so it clearly isn't a multiple of 8. Change it to start on 8388680 and you'll be set.

---

### Post by movieman on 2010-05-25
> **BMWolf said:**
> Should I be worried that the 'Spin_Up_Time' is so high for only 14hours of 'Power_on'?

That's smaller than the value for either of the 'Green' drives in my MythTV backend; I believe it's a time in milliseconds?

BTW, the load cycle count on my oldest two drives is less than 50, one with over 10,000 hours and the other with over 5,000 hours.

---

### Post by acesuares on 2011-01-22
> **bruceschaller said:**
> Hey all,

I found this topic rather frustrating, so I made a calculator in openoffice which shows the starting and ending sectors for an aligned drive. 

To use it, the desired size of the partition in whole gigabytes is entered, and starting and ending sectors are calculated.


Here's the link

[http://dl.dropbox.com/u/3235562/Advaced_Format_Calculator.ods](http://dl.dropbox.com/u/3235562/Advaced_Format_Calculator.ods)

I hope that it is useful!

Bruce S

Thank you for the tool! But shouldnt' the 2nd and 3rd partition begin on a sector divisible by 4^H^H 8? so, instead of adding 1, add 8?

I am not sure.

Ace

---

### Post by Cyber1000 on 2011-02-08
Just stumbled over this, I have a WDEARS10, works all fine. At the beginning I made a similar mistake like this script with my 2nd partition. damn was this partition slow, when I had a lot read/write accesses :-).
 
@acesuares you are right the calculation in the openoffice file is false!
 
The starting sector of every partition must always be dividable by 8! 
So for example if you open the file you get (out of the script) for 25 gb:
Sektor 64 to 52428864 (this would be 52428801 sektors, because you would count the first and the last, 52428801 is not dividable by 8, the next start sektor of 52428865 isn't either!)
 
For this example it should be sektor 64 to 52428863, sektor 52428864 to 56623167, 56623168 to ... . 
 
IF YOU FORMAT YOUR DRIVE WITH THIS SCRIPT IT WILL BE DAMN SLOW! (Sorry for being a little bit loud :-) )

---

### Post by srs5694 on 2011-02-08
> **Cyber1000 said:**
> @acesuares you are right the calculation in the openoffice file is false!
 
The starting sector of every partition must always be dividable by 8! 
So for example if you open the file you get (out of the script) for 25 gb:
Sektor 64 to 52428864 (this would be 52428801 sektors, because you would count the first and the last, 52428801 is not dividable by 8, the next start sektor of 52428865 isn't either!)
 
For this example it should be sektor 64 to 52428863, sektor 52428864 to 56623167, 56623168 to ... . 
 
IF YOU FORMAT YOUR DRIVE WITH THIS SCRIPT IT WILL BE DAMN SLOW! (Sorry for being a little bit loud :-) )

I've not looked at the script, but in terms of drive performance, it's the *start sector* that's important, not the partition length. Of course, if the length isn't a multiple of 8, there will be a gap between partitions if they're all to be properly aligned, but so long as each sector *begins* on a multiple-of-8 sector number, all should be OK.

---

### Post by Cyber1000 on 2011-03-15
Just stumbled again over this ...
I didn't have any concerns about the length (ok I calculated the length, but only because it's wrong and the next starting sector continues directly after the wrong-length-first-partition), therefore I wrote:
> The starting sector of every partition must always be dividable by 8! 

And thats the problem with the script, first partition seems ok, so if you only have one partition this script will work (but in this case you don't need a script), the other partitions won't be aligned correctly ...

---

### Post by rich1842 on 2011-04-23
I was trying to find info on using a WD Advanced Format disk drive for storage rather than system disk and found this:

[http://wdc.custhelp.com/app/answers/detail/a_id/5655/~/how-to-install-a-wd-advanced-format-drive-on-a-non-windows-operating-system](http://wdc.custhelp.com/app/answers/detail/a_id/5655/~/how-to-install-a-wd-advanced-format-drive-on-a-non-windows-operating-system)

I hope it may be useful to others.

Gparted is available in Ubuntu - for anyone who has not used it before you cannot just choose it to run from the apps menu - the system just thinks about it for a long time and nothing happens.

You need to open a Terminal window and type:  kdesudo gparted

By instructing GParted to run with KdeSudo, it is able to both find the Gtk libraries and run with elevated privileges.

You can also use that to open the 'Kate' text editor then choose 'open' to get into the file-tree (or whatever it is called) and change ownership, advanced permissions etc once you have installed your drive.

While I am on a rant - after all that you can use 'disk-manager' (get it from Synaptic and open it in the same way as the others) to choose mount attributes for your drive.

Probably everyone else knows all that but I didn't and it took ages to get all that together.

---

### Post by srs5694 on 2011-04-23
> **rich1842 said:**
> I was trying to find info on using a WD Advanced Format disk drive for storage rather than system disk and found this:

[http://wdc.custhelp.com/app/answers/detail/a_id/5655/~/how-to-install-a-wd-advanced-format-drive-on-a-non-windows-operating-system]("http://wdc.custhelp.com/app/answers/detail/a_id/5655/%7E/how-to-install-a-wd-advanced-format-drive-on-a-non-windows-operating-system")


I posted this comment to another thread in which you posted this link:

That's certainly better than what they used to say, which was that Linux  would use such drives with proper alignment by default! My main gripe  with that page as it is now is that it puts a lot of emphasis on kernel  versions, which really isn't very relevant. AFAIK, the Linux kernel has  never really been a stumbling block; it's the partitioning tools that  need to support such drives. In an ideal world, the kernel should be  able to properly identify the drives, but contrary to what that page  says, I have yet to see evidence that it can. I've got two such drives  myself, and I've tested several different kernel versions. The system  calls that are supposed to return the true physical sector size have  always told me that my Advanced Format drives have 512-byte physical  sectors, which they don't.

---

