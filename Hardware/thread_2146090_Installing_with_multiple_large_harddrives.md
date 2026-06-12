---
title: "Installing with multiple large harddrives"
date: 2013-05-17
forum: Hardware
---

### Post by mmoore on 2013-05-17
Hi everybody,

I have a quick question about how to install Ubuntu on the following system:

HDD1: 1 TB - Containing operating systems and /home
HDD2: 4 TB - Containing 2 data partitions (1.9 TB and 2.1 TB)
HDD3: 4 TB
HDD4: 4 TB - HDD3 and HDD4 have been combined into an 8 TB LVM
HDD5: 4 TB - currently not connected

If I use the regular Desktop Installer it gets stuck when trying to read the harddrives.
If I use the minimal Ubuntu CD it fails when installing the packages.

Is there a way I can install Ubuntu on this system?

Thank you very much for your help.

Kind regards,

manuel

---

### Post by oldfred on 2013-05-17
Were drives ever RAID or are they just LVM.
The standard desktop installer used to not work with either RAID nor LVM, since that was normally part of the server install version. They used to have an alternative installer that included the RAID & LVM drivers, but did away with that as they plan to add the full install with RAID & LVM to the desktop. But they did not complete it. 

If drives were ever RAID and you do not have RAID, you have to remove meta-data to get grub to install. Or you can install LVM support drivers to your Ubuntu live installer.

Have you then created partitions for / (root) /home & swap?
       sudo apt-get install lvm2
sudo apt-get install mdadm

Only if you do not have RAID.
Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
Also check BIOS for raid settings


Question. I normally do not suggest RAID for desktops, nor really know it, but I would think RAID would be better for your configuration. Any drive failure and your LVM is totally destroyed.
      
 Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328](http://ubuntuforums.org/showthread.php?t=1586328)

---

### Post by mmoore on 2013-05-17
Thank you for your reply.

I bought the drives new as they are being used in a new desktop computer.

I did partition HDD1 to hold four partitions. The first one being one parition for Windows, the second for "/", the third for swap and the last for "/home".
I do not intend to add /home to the LVM though.

I chose the LVM because I rather need storage space which can easily be expanded compared to redundancy. The LVM is going to be used to Virtual Machines which
are being used for test environments. Nothing which goes on there is irreplaceable. Bad to lose, but with that you can gain experience.

However, I do not think this problem comes from the LVM by itself. The situation was quite the same when all drives where being used individually.

Thank you very much for your help.

Kind regards

Manuel

---

### Post by oldfred on 2013-05-17
If the install drive is not LVM, it should just install. I do know with lots of drives & partitions it takes a while for the installer to see the partition info. I normally partition in advance with gparted, but it still takes a while. You may still need the lvm driver or it may just stall. 
Or just have one drive plugged in during install and add lmv2 driver after install so the installed version can see the lvm?

Post this:
       sudo parted /dev/sda unit s print

After installing lvm2 driver to live installer does it see partitions on other drives also?

---

### Post by mmoore on 2013-05-17
Let me verify that and get back to you.

I will be able to give you the answer on Monday, for I will not be at home over the weekend. But Monday I can tell you more.

---

