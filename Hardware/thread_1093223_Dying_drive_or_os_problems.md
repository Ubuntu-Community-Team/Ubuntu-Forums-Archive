---
title: "Dying drive or os problems?"
date: 2009-03-11
forum: Hardware
---

### Post by Jyncka on 2009-03-11
Hi, I'm still a beginner to linux and ubuntu.  I'm running hardy and I installed without any problem whatsoever except that one of my external drives isn't showing up at all.  Now any flash drive I plug in and my ipod work fine so I'm wondering if it's the drive and in any case is there anything I can do?

---

### Post by vanadium on 2009-03-11
It could be that the partition on your drive is not automatically been mounted anymore. That problem would be easy to solve. This frequently happens with ntfs formatted drives. If yours is not an ntfs drive, skip the following paragraph.

ntfs partitions that are not properly closed are not automatically mounted. The remedy is to connect the drive to a windows system, preferably have it checked usng the disk checking tools and then remove it properly from the system using the "Safely remove hardware" icon. Eventually, you should repeat that a couple of times. After that, such a partition will automatically mount under Ubuntu.

You can check wether your partition is seen by the operating system with the terminal command "sudo fdisk -l". If the drive is being recognized, data about the drive and the partitions on it will be in the output.

If it is not there, there is probably some hardware problem. this can range from the drive not been powerer, a faulty USB cable to an effective hardware failure of either drive or USB connection.

If it *is* there, then you should try mounting it using the command line: error messages during mounting can reveal why it does not mount automatically.

---

