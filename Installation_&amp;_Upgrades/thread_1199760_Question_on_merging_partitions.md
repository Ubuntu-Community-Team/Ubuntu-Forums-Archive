---
title: "Question on merging partitions"
date: 2009-06-29
forum: Installation &amp; Upgrades
---

### Post by thirdeye420 on 2009-06-29
Hey everyone,

I got my PC setup so I can dual boot windows xp and ubuntu.  Well, I never use my windows partition anymore, so I was thinking it would be nice to wipe that partition out and merge it with ubuntu so I have more HD space.  Just wondering if someone out there could point me in the right direction on how to approach doing this.

thanks

---

### Post by raymondh on 2009-06-29
> **thirdeye420 said:**
> Hey everyone,

I got my PC setup so I can dual boot windows xp and ubuntu.  Well, I never use my windows partition anymore, so I was thinking it would be nice to wipe that partition out and merge it with ubuntu so I have more HD space.  Just wondering if someone out there could point me in the right direction on how to approach doing this.

thanks

[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

When you installed Ubuntu, it (GRUB) overwrote unto the MBR.  You may have to re-install GRUB.  If so :

[https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)
[http://ubuntuforums.org/showthread.php?t=224351&highlight=fsck](http://ubuntuforums.org/showthread.php?t=224351&highlight=fsck)

Back up first.

Good luck.

---

### Post by thirdeye420 on 2009-06-29
alright,  I managed to format the partition that had windows xp on it to ext 2 (same as my linux partition).  how do i merge the 2 partitions?  I'd like it to be one big partition instead of 2.

---

### Post by raymondh on 2009-06-29
Hello thirdeye420,

[https://help.ubuntu.com/community/HowtoPartition#head-f2515acc4fa3a5b463d5a79bb834ded1f3daae4e](https://help.ubuntu.com/community/HowtoPartition#head-f2515acc4fa3a5b463d5a79bb834ded1f3daae4e)

As always .... back-up your files.

Do you want to do a straight-up merge using terminal?  If so, read this tutorial :

[http://www.howtoforge.com/linux_resizing_ext3_partitions_p3](http://www.howtoforge.com/linux_resizing_ext3_partitions_p3)

Another option is using gparted from liveCD (in live session mode), and, am ssuming you originally had a windows + ubuntu install (with Ubuntu installed after windows)

See this link for reference

[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)

1.  Right click SWAP and swap-off
2.  Click and delete the "old-windows-partition-that-is-now-formatted-in-ext2" and keep it unallocated
3.  Click on the original ubuntu partition > resize > drag slider to take up all the unallocated/free size. 

You may need to reinstall GRUB.  If so, here's a link/tutorial:

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

A third option is to wipe everything clean and do a clean re-install. If you do, I recommend you consider establishing a separate /home.

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

Good luck.

---

### Post by thirdeye420 on 2009-06-29
well i was succesful in getting the partitions merged and the MBR updated.  My only problem now is that the boot prompt still appears on start up (screen that allows you to choose to bbot win xp or ubuntu).  how do I make that disappear?

---

