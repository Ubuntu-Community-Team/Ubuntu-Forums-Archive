---
title: "problems with new hard drive and gparted."
date: 2009-09-13
forum: Hardware
---

### Post by the_artz19 on 2009-09-13
i am not sure if this is the right place to speak about issues with hard drives, but here goes.
i got a 1tb hard drive recently and have been trying to get it to work(also sadly only shows up as about 950gb). i have also recently installed ubuntu, and that was the only thing that seemed to recognise the drive was there(also it is a internal and installed correctly).
when running gparted, it asked me if i wanted it to be the main or extended partition(to which i cant say if it matters since i just want to store files on it in windows), and what type i wanted to format as. i wanted to make it ntfs so i could use it easier in windows, my main os. however that option was greyed out. i also tried making it fat32 first, but it was still grey.

if anyone has any idea of what might cause this i would be very apreciative.

---

### Post by jms1989 on 2009-09-13
first off, to format a drive to ntfs in linux, you need to install the ntfs-utils package.

Also, if you want to use it under windows than just format it under windows. Seeing as its an internal hdd, I'll assume its already installed.

Under winxp, just open your control panel, go to Performance and Maintenance, then Administrative Tools, then open Computer Management. Click on the Disk Managemant module, locate the disk, add a primary partition, choose to use the whole disk if you want, pick you file system and click done or whatever. 

A member on this forums as once said, "Disks to be used under windows should be formated by windows and disks to be used by linux should be formated by linux." (Or something along those lines. Point being, its easier to format a drive to ntfs under windows.

---

