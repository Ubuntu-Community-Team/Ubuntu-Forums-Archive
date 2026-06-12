---
title: "After partitioning, failed install caused 1 of 2 partitions to vanish"
date: 2009-08-09
forum: Installation &amp; Upgrades
---

### Post by altesk on 2009-08-09
Hi,

I had Windows XP and Ubuntu 8.04 dual-booting just fine on my computer for a long time.

Today I decided to wipe out both of them, and install them again fresh. I booted using my Windows installer CD, wiped out all partitions and reformatted the hard drive, then installed Windows successfully.

Using the same Ubuntu Desktop CD I used successfully before, I started the install of Ubuntu 8.04. I told it to split the hard drive about equally between Windows and Ubuntu (the install screen had that nice slider button that lets you graphically choose how much disk space to give each - I used that feature).

After that, it got 5% through the next phase of the install (copying files, if I remember right). It stalled there, I think because my CD-ROM drive would not read correctly (it seemed to do that once or twice, earlier in the day). I eventually shut down the machine.

So now the computer still launches Windows without problems, but Windows thinks the drive has about half the space it used to have. When I start the Ubuntu installation, and it reaches that screen where you choose how to partition the drive, the installer also sees only one drive with about half the space as before.

What is my best strategy for making the Ubuntu installer see all of the hard drive space? I'm guessing either a Windows or Ubuntu utility is required.

Thanks in advance for any guidance.:)

---

### Post by merlinus on 2009-08-09
Whilst running from the live cd, what does gparted show?  Also, you might post a screenshot.

---

### Post by presence1960 on 2009-08-09
hopefully you defragged windows after installing it because some of the worst fragmentation on windows occurs after an install. This may have prevented the partitioner from resizing your windows partition correctly.

Your second partition may be there. post the output of sudo fdisk -l or screenshot of gparted as merlin requested. if it is there you can use the manual install option or the use largest free space option on the Ubuntu install.

---

### Post by altesk on 2009-08-11
> **presence1960 said:**
> hopefully you defragged windows after installing it because some of the worst fragmentation on windows occurs after an install. This may have prevented the partitioner from resizing your windows partition correctly.

Your second partition may be there. post the output of sudo fdisk -l or screenshot of gparted as merlin requested. if it is there you can use the manual install option or the use largest free space option on the Ubuntu install.

I failed to defragment after installing Windows. But it looks like I got away with it; I have not experienced a problem as a result. I solved my own problem, and my new Ubuntu installation has a big partition.

I ended up using an Admin tool in Windows XP to delete the partition Ubuntu's installer created. It's quite easy. Right-click My Computer (either the desktop icon or the Start Menu item), select Manage. In the left column of the resulting window, click Disk Management. Click on the partition not being used by Windows, and delete it.

Then I launched the Ubuntu installer. When it asks how to partition, I chose "Guided - use the largest continuous free space". I could have chosen Manual, but I took the easy way out.

I did not have trouble with my CD drive, so it finished the install just fine.

---

### Post by presence1960 on 2009-08-11
Great! Enjoy Ubuntu.

---

