---
title: "How do I make partition to prepare an installation of ubuntu?"
date: 2006-01-14
forum: Hardware &amp; Laptops
---

### Post by Physicist on 2006-01-14
I got a new desktop:

Dell Dimension 9150 with configuaration as:
Intel Pentium D 820 (2.8GHz) w/Dual Core Technology 
1GB DDR2 SDRAM at 533MHz 
Dell USB Keyboard 
19 in (19 in viewable) E193FP Flat Panel Display 
128MB ATI Hyper Memory PCI-Express X16 (DVI/VGA/TV Out) Radeon X300 SE 
160GB Serial ATA Hard Drive (7200RPM) 
No Floppy Drive Requested 
Microsoft Windows XP Home Edition,Service Pack 2,English 
Image Restore 
Dimension Dell Support 
Windows Media Player 10 
Dell Owners Manual installed on your system,click on icon after system set-up to access 
Dell Direct Download 
Internet Search and Portal 
Dell USB 2-button mouse 
Integrated 10/100/1000 Ethernet 
16X DVD-ROM and 16X DVD+/-RW 
Integrated Audio 

and the preinstalled OS is Windows XP Home (English).

My questions are:

1. How should I make partition to the 150G harddisk for
a dual boot system, i.e. Ubuntu and WIndows ?
Would 
8G: linux sys
2G: linux swap
10G: windows system
60G: data 1
70G: data 2
be a good idea?

2. Once I have partition made, what should I do then to
install Ubuntu?

3. Would the dual core processor of my system affect
anything with a proper installation of a linux such as
Ubuntu?

Thank you very much.

---

### Post by andrewsawyer on 2006-01-14
Sounds like a good setup to me.  Not used Windows for ages though - how easy is it to setup so that the My Documents is on a separate partition?

Make sure Windows is installed first, as it will write over the MBR and you won't be able to boot into Linux until you mess about with it a bit.  Likewise, when you install Ubuntu, Grub will set Linux as the default boot (but will keep Windows shown).

Once you have the partitions set (you can use Partition Magic or whatever) then just stick in the Ubuntu CD.  _DON'T_ choose the auto partition as it will remove Windows.  You can go in and set all the partitions separately.  You shouldn't need to do anything with the Windows partitions unless you want to mount the windows data patition in linux.  If that is the case, format it as FAT32 rather than NTFS.

All should just install and be fine then.  You can set the data1 to mount as /home and data2 (windows data partition) to mount as /mnt/windowsdata or something.

I'm running an AMD Athlon 64 3800+ Dual Core and there was no difference installing Ubuntu on it than my Celeron.  I assume this is what you mean by the Q3?  There are no extra steps you need to take.

I hope this helps!

Andy

---

### Post by Physicist on 2006-01-14
So, right now I can just make partition to the 150G harddisk as

8G: linux sys
2G: linux swap
10G: windows system
60G: data 1
70G: data 2

by using Partition Magic ?

---

### Post by aysiu on 2006-01-14
Any reason in particular you have data 1 and data 2? Why can't you just have one huge partition with data on it? If I had your hard drive and wanted to dual boot (sharing documents between the two OSes), this is how I'd partition it:

13 GB NTFS for Windows XP
128 GB FAT32 for shared data between Windows and Ubuntu
6 GB Ext3 for Linux /
1 GB for the swap partition
2 GB Ext3 for Linux /home

This can actually be done with Ubuntu's own partitioning tool during the installation process--you do not need Partition Magic. If you want a free tool that's easy to use and fullproof, I'd suggest [using DiskDrake](http://www.ubuntuforums.org/showthread.php?t=114142) to partition before installing Ubuntu.

Basically, you have Windows XP on, then you defragment it and resize it, then install Ubuntu. For a full Ubuntu dual boot guide with explanations and screenshots, see the fifth link of my signature.

---

### Post by Lord Illidan on 2006-01-14
[quote=aysiu]Any reason in particular you have data 1 and data 2? Why can't you just have one huge partition with data on it? If I had your hard drive and wanted to dual boot (sharing documents between the two OSes), this is how I'd partition it:

13 GB NTFS for Windows XP
128 GB FAT32 for shared data between Windows and Ubuntu
6 GB Ext3 for Linux /
1 GB for the swap partition
2 GB Ext3 for Linux /home

This can actually be done with Ubuntu's own partitioning tool during the installation process--you do not need Partition Magic. If you want a free tool that's easy to use and fullproof, I'd suggest [using DiskDrake]("http://www.ubuntuforums.org/showthread.php?t=114142") to partition before installing Ubuntu.

Basically, you have Windows XP on, then you defragment it and resize it, then install Ubuntu. For a full Ubuntu dual boot guide with explanations and screenshots, see the fifth link of my signature.[/quote]

I think this is a better solution, imho:

20 GB NTFS - windows xp
100 GB FAT32 - shared
10 GB EXT3 - Linux /
1  GB SWP
rest /home

---

