---
title: "Nonsequential WinXP External Drive Letter in VMware"
date: 2008-09-04
forum: General Help
---

### Post by raywood on 2008-09-04
I have a hardware problem using VMware Workstation 6.0 on 64-bit Hardy (Ubuntu 8.04), in a dual-boot Windows XP setup.  I realize that qualifies me for about three other forums, but before I get forwarded from one to the next, I thought I'd better start in a general-purpose forum.  Besides, y'all have been very friendly and helpful so far, which I appreciate.

I have several partitions.  Of course, when I boot the system in WinXP, Windows assigns drive letters to each, starting with C.  I make an exception for my external drive:  I manually assign it to be drive O.  The reason is that I have some Windows software that is looking for a specific drive letter, and if I change the number of partitions, the external drive's letter changes, and then the software doesn't work unless I go in and make revisions that take time.

Sometimes I swap drives in the external drive enclosure.  When I do that, WinXP forgets that the external drive was drive O.  Until I go into Windows Disk Management and change the drive letter, it is now drive H or I or whatever, and my software doesn't work.

But I am only able to change the drive letter by booting WinXP natively.  If I boot WinXP within a virtual machine in VMware running on Ubuntu, the external drive is a network drive, not a local drive, and Disk Management doesn't see it.  Ubuntu sees it just fine, but I can't change the external drive to be drive O for purposes of my work within the virtual machine.

I'm still a little unclear on shared drives and network drives.  It doesn't seem like it's a Windows problem.  In Windows Explorer, I select Tools > Map Network Drive, and navigate to the right place, and the drive's name (OFFSITE) is visible there.  I can map it to be any letter -- O or I or whatever -- but unfortunately it's still invisible to WinXP in the virtual machine.

Confusing!

---

