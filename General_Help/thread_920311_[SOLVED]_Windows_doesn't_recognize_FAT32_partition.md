---
title: "[SOLVED] Windows doesn't recognize FAT32 partition"
date: 2008-09-15
forum: General Help
---

### Post by Piraja on 2008-09-15
Dear all,

I installed Fluxbuntu on a 4 GB pendrive and it works beautifully. However, as I need to exchange files with Windows XP, I created a FAT32 primary partition on the pendrive. Now as I plug in the pendrive in WinXP and double-click on the drive icon, Windows tells me the "disk is not formatted". Formatting it in Windows is out of the question, because Windows only seems to know how to format the whole pendrive.

[EDIT: The last phrase was not precise: Windows does present the option of formatting only the partition-in-question. If I go to "Control Panel > Admin. Tools > Computer Management > Disk Management" I can see the partitions on the pendrive. However, when I try to format the ca. 800 MB partition - which I already formatted in Linux to FAT32 - I get a message telling me that the device cannot be formatted because it's not enabled, and to enable it I must reboot. At the same time, the "Device Management" shows that the USB pendrive is indeed enabled. Rebooting doesn't affect the situation.]

This is rather surprising. Even though there are lots of things Windows can't handle, one would suppose it recognizes an MS file system! For partitioning and formatting, I used both GParted and OpenSuse 11 LiveCD's default partition editor (Yast/Expert Partitioner). First I made the mistake of making the FAT partition logical, but as I realized it's not recognized by Windows, I made the necessary changes and made it primary.

Should the d***ed FAT32 reside on the first partition of the USB pendrive in order that Windows recognizes the stuff's there? Changing the partition order would be a bit frustrating, including the need to re-edit the menu.lst file, etc.

By a quick search, I could not find specific information related to this issue. 

Thanks for reading this, and extra special thanks for anyone who can help!

---

### Post by baccilus on 2008-09-29
I had been facing the exact same problem. Now I realized that windows can recognize only the first partition, i.e. sdx1. This is a good thing in a way because your Linux partion will always be left alone by windows, friends who may borrow your Pen drive as well as viruses.
Trick is to install Linux on any other partion except sdx1.
(x can be b, c, etc depending upon number of hard drives you have)

---

### Post by C.S.Cameron on 2008-09-29
I have done a bit of experimenting with this.
The only way I have been able to get windows to recognize a fat partition on thumbdrive is to format in windows then install Ubuntu.
When you get to partitioning use:
Guided, resize ...and use remaining space.
Then drag the bar right to show how much FAT you want to keep.
Wish I knew a way to retro install a windows partition, but I haven't found one.
Once you have Ubuntu installed you can re-size and move your partitions no problem.

While you are at it you might also consider manual partitioning option.
That way you can also make a home partition. 
With manual partitioning make sure you do not format the windows partition.

---

### Post by Piraja on 2008-09-29
Thanks! I'm marking this thread as solved.

---

### Post by Piraja on 2008-10-02
Just one more thing... or a couple.

There are interesting and (I believe) useful hints at the [Pendrive Linux]("http://www.pendrivelinux.com/") website, including a tutorial for [sharing files between Windows and Linux]("http://www.pendrivelinux.com/2008/05/05/sharing-files-between-windows-and-linux/"). [Virtual Machine Emulation]("http://www.pendrivelinux.com/category/virtual-machine/") might come as handy when you want to or have to use both systems and share files among them. 

By the way, I always partition manually (well, I suppose my first Ubuntu installation way back - way back in May - was "guided") and have made separate home partitions on my desktop (external HDD installation) and laptop PCs. I find it a very reasonable thing to do, too.

---

