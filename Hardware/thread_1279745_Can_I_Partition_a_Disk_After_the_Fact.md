---
title: "Can I Partition a Disk After the Fact?"
date: 2009-10-01
forum: Hardware
---

### Post by mulluysavage on 2009-10-01
I want to dual-boot. I have a single HD with a single partition running ubuntu 8.04. Can I now partition the disk for dual-boot?

---

### Post by louieb on 2009-10-01
Dual boot what? Sure you can shrink the existing partition(s) to create unallocated space for a new partition.  The type of new partition you will need depends on what OS your going to install. Windows needs  a primary partition. Another Linux distro can go in a primary or logical partition.

---

### Post by fela on 2009-10-01
> **louieb said:**
> Windows needs  a primary partition.

I didn't know that, that sucks! Really it does!

---

### Post by mulluysavage on 2009-10-01
I want to add an XP partition. Could I? If so, how?

---

### Post by drs305 on 2009-10-01
> **mulluysavage said:**
> I want to dual-boot. I have a single HD with a single partition running ubuntu 8.04. Can I now partition the disk for dual-boot?

Sure you can. As louieb said, put MS on a primary partition. You will have to use the LiveCd or another rescue-type CD to do the partitioning with gparted, since you normal install can't be running when you do the partitioning.

As with any change in the partition table, make sure you back up crititcal data before you change the partitions.

I wrote a guide about expanding the / partition. For you it will be easier since you are shrinking it and you won't necessarily be dealing with extended partitions. Nevertheless, some of the recommendations still apply.
[Expanding an Ubuntu System Partition]("http://ubuntuforums.org/showthread.php?t=1219270")

Also, after installing Windows, you may lose your Grub setup. Here are some links on how to restore it:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RestoreGrub]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RestoreGrub")

[How to restore the Ubuntu/XP/Vista bootloader]("http://ubuntuforums.org/showthread.php?t=1014708")

---

### Post by mulluysavage on 2009-10-01
Great - so let me get this straight:

1. Boot from LiveCD

2. Shrink my partition/create 2 partitions

3. Make the new, blank partition a primary

4. Make the old partition a logical

5. Set up GRUB to prompt me each time with the option to boot to either.

Right?

---

### Post by MedianMajik on 2009-10-01
Now would be a good time to invest in useful backup/partition live CD's.  Consider, Download, and Burn the following:

[Parted Magic](http://partedmagic.com/)
[SystemRescueCD](http://www.sysresccd.org/)
[Clonezilla](http://clonezilla.org/)

Also useful is an app called ReMasterSys, which only takes a couple clicks to create live cds of your current desktop.  I would do this at the very least before potentially wasting your desktop.

---

### Post by drs305 on 2009-10-01
> **mulluysavage said:**
> Great - so let me get this straight:

1. Boot from LiveCD

2. Shrink my partition/create 2 partitions

3. Make the new, blank partition a primary

4. Make the old partition a logical

5. Set up GRUB to prompt me each time with the option to boot to either.

Right?

You can have 4 primary partitions. You would *not have to* make the old partition a logical one. Also note, you have to create an extended partition first, then logical partitions are placed *within* it.

Having logical partitions are a good idea because you are not limited to 4 as you are with primary partitions. (However, the extended partition *is* one of the 4 primary partitions.

The easiest thing to do for now without moving things around would be to just make another primary partition for Windows, leaving you with 3 primary partitions (Ubuntu, swap, Windows). If you have left over space, you can make an extended partition, then a logical partition including the extra space. If you do this, make sure you leave 'growing room' for both Ubuntu and Windows. It's much easier to shrink a partition than to expand one.

How to set up partitions is pretty subjective. There are lots of ways to do it.

As a point of reference, if windows preexists on a computer, here is what Ubuntu does:
1 Windows (Primary)
2 Extended Partition
5 Ubuntu (Logical)
6 Swap (Logical)

---

### Post by mulluysavage on 2009-10-01
One of my concerns is that there is data all over the disk - is this likely? It's a 320GB disk and about 30G is used by Ubuntu I think. Would a partitioning tool be able to move data appropriately? Is it unlikely to be a problem?

---

### Post by drs305 on 2009-10-01
> **mulluysavage said:**
> One of my concerns is that there is data all over the disk - is this likely? It's a 320GB disk and about 30G is used by Ubuntu I think. Would a partitioning tool be able to move data appropriately? Is it unlikely to be a problem?

As always, back up any data files. In Ubuntu, fragmentation is not generally an issue. If you use Gparted to reduce the size of your Ubuntu partition you shouldn't have a problem. Things can and do go wrong (power interruptions, etc) of course, but it is rare.

You get to Gparted from the LiveCd via System, Administration, Partition Editor (or Gparted if using Karmic).

---

### Post by louieb on 2009-10-01
It would be good to learn about partitions. Its not hard there are only 3 kinds. Primary, extended and logical. I put this page together a while back. [Nuts n Boldt: Partitions 101]("http://louboldt.com/ilinuxpart.htm") 

And while your at it understanding the boot process - MBR, boot sector, boot loader. is a good to know too.  Found this page a few weeks back really like it. Explains what happens when Linux, XP and Vista/Win 7  boot. [Multibooters, Pictures here worh 1000+ words]("http://www.multibooters.co.uk/multiboot.html") 

As for changing partitions around on a hard drive with data on it - there is always a chance the data could get corrupted - its rare. Don't do it in the middle of a thunderstorm - a power outage - well... Pays to take a backup  1st.

---

