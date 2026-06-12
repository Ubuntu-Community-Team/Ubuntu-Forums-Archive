---
title: "Partition table/MBR corrupt, what is a good utility to fix with"
date: 2010-08-11
forum: Hardware
---

### Post by hotwheelharry on 2010-08-11
Hey!

I was trying to install OSX SnowLeopard on my laptop and it almost worked! I ran Disk Utility in the installer to format my extra partition as Mac OS Extended. It worked fine. But I realized that the partition scheme had to be GPT and the SL installer decided to not let me install it while using the "MBR" scheme. When I tried to reboot into windows to find out how to convert to GPT, BIOS said "no operating system found." I realize this doesn't have to do with Ubuntu, but I'm writing this and trying to fix the problem using an Ubuntu Live CD. So, I would like to get Ubuntu tools to fix it with. Also I've wanted to use linux more in depth, maybe now is a good time to learn. :D. Here is what I've tried so far.

ms-sys to rewrite the MBR.
- The HD was actually readable before I did this, and then I did this using the Windows 7 arg and everything seemed good. Then I rebooted and it said the same error. Then I loaded up Ubuntu and noticed that the HDD was not readable or even recognized until I looked in gparted. It said format unknown. In fdisk it says HPFS/NTFS. It was originally NTFS of course.

How did the Snow Leopard installer change that anyway. From NTFS to HPFS/NTFS. I only used it to format another partition to MacOS Ext. which worked fine. The windows partition was somehow affected.

Anyway, I tried ms-sys one more time and then rebooted. Now it says "partition table invalid" or something like that.

Oh, I almost forgot, in gparted I changed the flags for the partitions. The mac partition had the boot flag. It isn't supposed to boot from that one so I changed it so the windows partition had the boot flag instead. That was when the error changed from "OS not found" to "partition table invalid."

Any thoughts on how to rescue my windows partition? :D I could really use the data back LOL!

Also, while I'm at it, is there any way to change the partition scheme from MBR to GPT without deleting the whole drive first?

PS. I don't have a windows CD.

---

### Post by mastablasta on 2010-08-11
Don't know much about Win7.
 
But in WinXP you can use the CD to run system console where you can then type 
 
fixmrb  
 
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx?mfr=true)
 
it might be that you will have to reformat the partition, since you changed it into some other format that windows doesn't know how to read.
 
[http://support.microsoft.com/kb/100108](http://support.microsoft.com/kb/100108)
 
i hoope you backed up the data before playing with operating systems....
 
Also there is a Linux disk recovery distro somewhere on the net (check wikipedia linux distributions). maybe it could help...

---

