---
title: "[SOLVED] Partitioning NTFS drive for 8.10 install"
date: 2008-12-28
forum: Installation &amp; Upgrades
---

### Post by airjaw on 2008-12-28
Hey guys,wondering if I can get a quick answer here..

This is my first time installing 8.10 after an XP installation, on the same hard drive.

right now my HD is formatted entirely NTFS.  I want to partition out 10gb for ext3 for root and 2gb for swap.

I'm in the 8.10 setup right now and its telling me that in order to make new partitions out of the NTFS, its going to wipe out any existing partitions.  Doesn't this mean I'd have to install WINXP again? Is there any way to avoid this?  Do I have to exit setup, go back to liveCD, and use Gparted?  Cuz it doesn't seem intuitive that way..

Thanks.

---

### Post by taurus on 2008-12-28
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
[http://www.psychocats.net/ubuntu/dualboot](http://www.psychocats.net/ubuntu/dualboot)

---

### Post by airjaw on 2008-12-28
Weird, but I don't get an option to resize my partition.  Meaning, there is no way to get a new partition of ext3 without completely killing my existing NTFS partition.

I'm not sure why this is the case.

edit;: might be because setup detected errors on my HD.  apparently some of it is corrupted and apparently failing

---

### Post by taurus on 2008-12-28
Before you resizing your harddrive, backup your personal files first.  Then, boot into windows and run the defrag of your harddrive a couple of times.

---

### Post by airjaw on 2009-01-10
The issue was that my hard drive has (toomany) bad sectors.

---

