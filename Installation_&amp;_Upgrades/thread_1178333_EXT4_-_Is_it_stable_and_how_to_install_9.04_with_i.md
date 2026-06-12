---
title: "EXT4 - Is it stable and how to install 9.04 with it."
date: 2009-06-04
forum: Installation &amp; Upgrades
---

### Post by ubuwatson on 2009-06-04
I am about to install Ubuntu 9.04 on another machine (notebook).  I have read mixed reports (though mostly positive) about EXT4.  Is it worth installing it on my notebook computer ?  And if so, how do you go about installing 9.04 (fresh install) using EXT4.  I read a couple of posts on the subject but unfortunately the information was rather haphazard - i could use some step by step screen shots or something of that nature.

Thanks,
Daniel

---

### Post by cariboo on 2009-06-04
I have ext4 partitions on 3 computers, all are running with zero problems. A note of caution though, if your data is important use something else, and wait until ext4 is installed by default.

On my server only the boot partition is ext4 the rest of the 1.2Tb are formatted as xfs. Xfs is just slightly slower than ext4, but it has been well tested and is quite reliable.

To format your partitions as ext4, when you get to the partitioning section of the install choose manual partitioning. This is the only way to format your partitions as ext4.

---

### Post by raymondh on 2009-06-04
Same experiences with ext4 .... so far so good though I tend to back-up to an external ....

---

### Post by zika on 2009-06-04
If You want to be on safe side add rootflags=data=ordered to Your boot line to have stuff written to disk before journal is written, the way Linus likes ... :) (and to altoptions and defoptions in /boot/grub/menu.lst, followed with update-grub)

---

### Post by quantum64 on 2009-06-04
Have you noticed any performance increases? I tried reading some of the benefits to EXT4, but I did not get a clear idea of what the benefits are just yet.

---

### Post by mrtomservo on 2009-06-04
I installed two separate 9.04's with EXT4 and EXT3 on the same hard drive.  I found that EXT4 was noticeably faster than EXT3.  Horror stories kept me from using EXT4 as my primary OS filesystem, as I do a lot of work on my pc.  Of course I backup, but still.  I made an extra partition for gaming, and intend to use EXT4 for that.  I should note that the month I ran EXT4 I had NO problems what so ever.

---

