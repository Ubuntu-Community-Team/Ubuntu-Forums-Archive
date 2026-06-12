---
title: "Disk Partitions in Ubuntu"
date: 2009-05-01
forum: Installation &amp; Upgrades
---

### Post by budoor on 2009-05-01
Can anyone explain for me this picture

what does every partition mean and why it has the following size???

[IMG]http://upload.traidnt.net/upfiles/8nt28034.jpg[/IMG]

Please help .. I need to reply by today ..

---

### Post by budoor on 2009-05-02
please help me :(

---

### Post by Herman on 2009-05-02
Your hard disk is called '/dev/sda' by Linux and it's relatively small by modern standards, only 8.0 GB.

The first partition is called '/dev/sda1', and it is formatted with the ext3 file system.
It's 'mount point' is /, so this is your main operating system partition. It's already about 1/3 full of files and data. I would guess that there probably is mainly the operating systems and a few installed programs and not too many files for the used space to be that small.
The first partition is a 'Primary' partition.

We can have up to four primary partitions in a hard disk. 
We can between one and three primary partitions plus one extended partition.
An extended partition can contain a number of logical partitions inside it, chained together in a series. In that way we can have up to about 16 partitions per hard disk instead of only four.

The partition numbers 1,2,3 and 4 are reserved for primary partitions.
An extended partition is a special kind of logical partition.
Normally, the partitions are numbered sequentially in the order they are created in and not according to their actual position on the hard disk.
Partitions numbered 5 and greater are always logical partitions.

Your second partition is an extended partition.

Your number 5 partition is a logical partition and it is designated for use as a linux swap area. A 'swap area' is an area of the hard disk reserved for the operating system to write files to that would otherwise need to be stored in the main memory. Generally, the commonly recommended swap area size used to be around half to two-thirds the size of your RAM.
If the motherboard has less than around 512MB of main memory, the swap area begins to become more important. Some computers with very small main memory can be very slow or may freeze without sufficient swap area.  The Windows equivalent of 'swap area' is called a 'page file'. Most Linux users prefer it to be in a separate partition. Actually, it can instead be located inside the main operating system as a folder, and some people prefer it that way.
If the computer has 1 GB or more of RAM, the swap area probably will not be needed very often.
We can control how much the operating system prefers to use the swap area compared with the memory by changing the 'swappiness' settings. It's debatable whether or not you can speed up your computer's performance by increasing or reducing swappiness, and under what kinds of usage it's important.
Another use of the swap area is to store files from the memory when the operating system is put into 'hibernation' mode, (instead of shutting down). The swap area should be at least twice the size of the RAM if you want to use it for that.

Basically, I would say that looks like a good, sensible partitioning scheme, and it looks fairly standard. 

Regards, Herman :)

---

### Post by Herman on 2009-05-02
You asked why the partitions have the sizes they do.
I forgot to say that the / (root) partition, /dev/sda1 in your case, should be as large as possible unless some other partition needs the space.

The file system in the / (root) partition works best when it is less than 80% filled with files. Over 80% full, fragmentation can begin to become a problem. Otherwise, Linux file systems never need to be defragged. There's no defragmenter for Linux, the way to defrag is to move all the data to some other partition and copy it back again. If you have the room to do that you probably had the room to store some of your data in the other partition and avoid the whole problem in the first place. Actually, it's extremely rare to need to defrag in Linux, I have never needed to and I've been using Linux for years.

Some people like to divide the / (root or main operating system partition), in two and use a separate partition /home.
A few even divide the operating system up into many small partitions, almost one partition per directory.
The supposed advantage of sub-dividing the hard disk up into many small partitions is supposed to be to preserve data in case a file system in one partition becomes corrupted somehow. The operating system is supposed to be easier to repair that way. Only some small part of it needs to be replaced.
The original minix file system had a size limit of only [1 Gb for a version 2 file system, and 64 Mb for a version 1 file system]("http://minix1.woodhull.com/faq/filesize.html").
With modern journalling file systems like Ext3 or Ext4, partitions can be very large, and it's rare for a file system to be damaged beyond repair except if there's a problem with the hard disk itself. Therefore it's best to just install in one single large partition, but keep a backup of all your files for safety. The advantage of having everything in one partition is that directories are always flexible in size. With partitions you need to guess how small or large to make each partition beforehand and then when they get filled up you have the problem of how to resize them or cope with an installation that's limited in some way.
Therefore I think in these modern time it's best to install with as few partitions as possible, I even like having my swap in a file instead of a separate swap area.

---

