---
title: "looking for a lable&amp;advice"
date: 2013-01-19
forum: Hardware
---

### Post by jcalemusmcd on 2013-01-19
so i first want to find a label. what is the listed "name" for 5 hard  drives, 3 running separate OS's, 1 as utility back up, and the last as  "whatever" storage.
or is there even a name for such a configuration?

next i'm trying to find advice for HOW to make this all happen
currently i am finding it EXTREMELY hard to accomplish this goal, and absolutely no documentation on it's setup or use.

any suggestions?

---

### Post by tlhIngan on 2013-01-19
Why do you want so many hard drives instead of multiple partitions?
Why would you want 3 different OS's?

---

### Post by grahammechanical on 2013-01-20
I am not sure of what you want. Having 3 OS on three separate drives seems to me as a waste of space because you only have drive left for "whatever" storage. If you want this 5th drive to be accessed by all 3 OSes then you will have a problem if an OS cannot read the file system of the drive.

Here is something to look at: LVM

[http://www.tutonics.com/2012/11/ubuntu-lvm-guide-part-1.html#.UPwXJqmKjVs]("http://www.tutonics.com/2012/11/ubuntu-lvm-guide-part-1.html#.UPwXJqmKjVs")

But there will be problems if the other OS are not Ubuntu.

Then there is RAID

[https://wiki.ubuntu.com/Raid]("https://wiki.ubuntu.com/Raid")

Are you aware that Ubuntu will let you select which OS to boot from at boot time?

[https://help.ubuntu.com/community/DualBoot]("https://help.ubuntu.com/community/DualBoot")

I am guessing as to what you want to do and what it is that is making it so hard to do.

Regards.

---

### Post by oldfred on 2013-01-20
My desktop has 4 hard drives, old XP, old Ubuntu, larger drive with data & many older Ubuntus & a new test install or two, and my newer SSD with 12.04 & 12.10. I try to install the boot loader to the same drive as the install, so drive can boot even if other drive fails. Every install is in 25GB / partition with /home but all data is in separate data partitions.

I prefer to have an operating system on every drive. Somewhat like this logic except I use Ubuntu.
       Creating a Dedicated Knoppix Partition for large drives
[http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm](http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm)
Except I have multiple Ubuntu installs and rotate newest install from drive to drive.
    
You just use any of the multiple installs to second drive as it does not matter once you get beyond one drive. 

       Install to external drive. Also any second drive.
Installer version has not changed much so still a good guide except I do not recommend the separate /boot for most systems. Older systems may need it. And some with very large / (root) partitions. BIOS/MBR not for UEFI
[http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/](http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/)
Installing Ubuntu in Hard Disk Two (or more) internal or external Lots of detail - now alternative (text based) installer
Different versions have slight difference in install screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB boot loader?
[http://members.iinet.net.au/~herman546/p24/041.png](http://members.iinet.net.au/~herman546/p24/041.png)

---

### Post by jcalemusmcd on 2013-01-21
thank you all for your reply's
i will have to go through these very thoroughly to learn the fine points of your suggestions

this might take me some time

---

