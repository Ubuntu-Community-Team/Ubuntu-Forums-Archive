---
title: "XFS or EXT4"
date: 2009-03-19
forum: Installation &amp; Upgrades
---

### Post by marcelkoopman on 2009-03-19
I've read that EXT4 has data loss issues which will be fixed in kernel 2.6.30.

Anyone here uses XFS and should I prefer that one instead of EXT4?

---

### Post by zvacet on 2009-03-19
> Alpha 6 supports the option of installing the new ext4 file system. ext3 will remain the default filesystem for Jaunty, and we will consider ext4 as the default for the next release based on user feedback

Taken from [here.]("https://wiki.ubuntu.com/JauntyJackalope/TechnicalOverview")

---

### Post by adzik on 2009-03-19
I would say stick with ext3.
I use XFS, but that is because it is for network application.
Ext3 is a touch slower than XFS, but more stability/recovery tools.
Ext4 should be a little better, but for everyday basic computing I wouldn't bother yet. Let it prove itself out in the world a bit more.

---

### Post by barney_1 on 2009-04-13
I'm planning to switch from XFS to EXT4 on one partition.

I have an HTPC on which I run mythtv (mythbuntu).  I plan to use the recording storage partition as my EXT4 guinea pig when I upgrade to Jaunty.  I guess I'm the "out in the world" that adzik was referring to.

---

### Post by DenysT on 2009-04-13
Guess I'll try EXT4 as I have a test PC that I built specifically for learning Ubuntu and have nothing to lose as I was going to clean install instead of upgrading from 8.10. Nothing resides on the machine as far as data goes and in the process of learning I have managed to goof a few things up, got some fixed but now that I have a better feel for the OS I'm going to start over with Jaunty and go from there. So why not go with EXT4?

---

### Post by HeadHunter00 on 2009-12-04
Never mind. With kernel 2.6.31-7, ext4 has become faster and more stable than xfs.

---

### Post by avdheiden on 2010-01-17
Your question is impossible if you don't describe the configuration and purpose of the partition involved.
Without that information, only general issues can be discussed and no advice is possible.


XFS had the advantage of speed over Ext3 and Ext4. It is also known to remain fast even if large portions of the disk are filled with very small files. Therefore, databases thrive on XFS filesystems.
Both filesystems are journaling and are generally equal when it comes to reliability and stability as far as I know from my own experience and that of others I know.

XFS has two minor disadvantages. The first is that you can't make an XFS partition bootable (but why would you do that since it's a journaling system !) and the other is that even though you can increase the partion size live, you can't decrease it's size. Not even offline.

As an example, my configuration for desktop purposes

/boot         Ext2
/var          Ext4
/var/log      Ext4
/             XFS
/home         XFS

hope this information is helpful to you

---

### Post by John Bean on 2010-01-17
> **avdheiden said:**
> hope this information is helpful to you

You do realise you're responding to a question asked nearly a year ago?

---

### Post by Sef on 2010-01-17
> Quote:
                                                                      Originally Posted by **avdheiden**                     [[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=8679763#post8679763")                 
                 *hope this information is helpful to you*
                                 
You do realise you're responding to a question asked nearly a year ago?It's ok.   This post has been going on for a while.  Last post before avdheiden's was this past december.    If the last post had been a year ago (2008) then I would have locked it for necromancing.

---

### Post by Kangarooo on 2010-04-25
What i did for one friend just now is Crunchbang on 40gb drive
/boot/ 100mb
/swap  512mb (couse his ram is 512)
/      5gb (for programms and system)
/home  all the rest drive space ~32gb (for data)
all drives are XFS exept swap (couse for swap its not configurable at least on istallation)
After all updates && sudo aptitude remove firefox old kernels were removed (couse aptitude removes unnecesery packages/not in use/left with no use) boot has 55mb free space and / has 3gb free space and since he will only use chrome and maybe music i could even make / just 3gb

Computer counting from grub to usefull/active system takes 23seconds to boot

---

