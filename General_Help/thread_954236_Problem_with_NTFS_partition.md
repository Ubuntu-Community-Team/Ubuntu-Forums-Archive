---
title: "Problem with NTFS partition"
date: 2008-10-21
forum: General Help
---

### Post by aarteaga on 2008-10-21
Hi all!
I bought a new external HD. When tried to make the partition and format stuff in Windows, using PartitionMagic, the program gave an error message; something about wrong partitions I think.

I though "damn Microsoft, let's try Ubuntu". So restarted in ubuntu and installed partman. Everything seems to go fine, in vain tried to make an ntfs partition on my new HD, so closed the partman and tried cfdisk.This is the message I got:
FATAL ERROR: Bad logical partition 6: enlarged logical partitions overlap

Now, I tried again with partman, and have an error awaiting for me:
/lib/partman/auto.d/10initial_auto: 31: udpkg: not found

and another line I couldn't recover because, if I try again to run the program, it halts at 53% in loading whatever its loading.

This is my partition list obtained from gparted:

/dev/sda1     fat16        47MB       DellRestore
/dev/sda2     ntfs         58.66GB    Windows
/dev/sda3     ext          47.03GB    Any idea?
   /dev/sda6  linux-swap   1.86GB
   /dev/sda7  ext3         235.3MB    /boot
   /dev/sda8  ext3         6.34GB     /
   /dev/sda9  ext3         12.08GB    /home
   /dev/sda5  ntfs         26.52GB    Windows backup
/dev/sda4     fat32        6.34GB     DellRestore

I guess there is any problem with the partitioning, but don't have any idea about how to solve it or even find it. Before making new partitions in order to install ubuntu a few months ago, the partition for windows backup was bigger; the main windows partition remains the same as always.

My computer is a Dell Inspiron E1505, originally with Windows XP Media Center (wich explains the tiny Dell partitions). Actually my computer seems to work fine (taking out the blue screens of death I'm getting lately), but I want to solve this issue before I start to miss data from my disk.

---

### Post by Pro-reason on 2008-10-21
I've never used partman.  Have you tried simply using GParted for the partitioning?

By the way, NTFS is evil.

---

### Post by aarteaga on 2008-10-21
Well, my laptop came with windows so I had no choice with NTFS. By the way, I have the idea that NTFS is better than FAT, why do you think is evil? :s

Actually, I am not sure if the problem is with the NTFS partition. Today I could use PartitionMagic (in Windows) again, and it reports the whole drive as BAD (whatever it means). The problem seen to be an overlapping issue.

I am asking in this ubuntu forum because I think was in the ubuntu installation that the problem started; before that the partitions were the ones that the laptop came with.

I could erase all the partitions and start again, but then I'll lose the recovery information in the Dell partitions along with my licensed windows (If paid for that I won't sent it into trash, even if it's garbage).

Thaks in advance for your help.

---

### Post by Pro-reason on 2008-10-21
NTFS is better than FAT for Windows systems.  The are both crappy for non-Windows systems.  I use [ReiserFS]("http://en.wikipedia.org/wiki/ReiserFS") for my main Ubuntu partition, and [ext3]("http://en.wikipedia.org/wiki/ext3") for others.  There are [Windows]("http://ext2fsd.sourceforge.net/") [drivers]("http://www.fs-driver.org/") [available]("http://uranus.it.swin.edu.au/~jn/linux/ext2ifs.htm") for ext3, so that you can access files when you occasionally need to use Windows for something.

PartitionMagic doesn't know very much about non-Windows partitions.  It doesn't always view them correctly.  It will sometimes get confused and decide that a whole drive is “BAD” because it can't understand the contents.  GParted is a much more advanced tool.

The “ext” partition in your list is not to be confused with ext3.  It is not a filesystem.  It is an [extended partition]("http://en.wikipedia.org/wiki/Extended_partition") that serves as a holder for your [logical partitions]("http://en.wikipedia.org/wiki/Logical_partition").

You should boot into Ubuntu and see if you can use GParted and *[fsck]("http://www.manpagez.com/man/8/fsck/")* to fix the drives.

---

### Post by caljohnsmith on 2008-10-22
You can use testdisk to try and recover your partitions. When you boot your Live CD, open a terminal (applications > accessories > terminal), and first post:
```
sudo fdisk -l
```
Also see if you can mount your backup partition and Windows partition:
```
sudo mkdir /mnt/sda1 /mnt/sda2
sudo mount /dev/sda1 /mnt/sda1
sudo mount /dev/sda2 /mnt/sda2
ls -l /mnt/sda1 /mnt/sda2
```
Where "-l" is a lowercase L, not a one. Please post the output of the above commands.

Then enable all your repositories in System > Admin > Software Sources, and download and run testdisk with the following commands:
```
sudo apt-get install testdisk
sudo testdisk
```
After starting testdisk with the above command, choose "no log", select HDD and "proceed", "Intel", "Analyze", and see what it shows for your HDD and what errors it might give. Please post the output of that screen. Then do "proceed", Y/N depending on if you have any Vista partitions, hit enter, and select "search!" so it does a deeper search, which could take a while. Post the output of that screen if you would like help recovering your partitions. :)

---

