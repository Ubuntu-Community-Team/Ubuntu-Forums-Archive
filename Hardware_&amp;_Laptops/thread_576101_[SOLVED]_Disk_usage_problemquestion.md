---
title: "[SOLVED] Disk usage problem/question"
date: 2007-10-14
forum: Hardware &amp; Laptops
---

### Post by theonlykman on 2007-10-14
Hi,
I was trying to install vista using virtualbox and, stupid me, I ran out of space on my partition as the installation filled up the disk image (the partition is only 9.6 GB and according to Disk Usage Analyzer about half of it was free before the installation). So, the next time I try to log in I can't because the disk is full. Whoops. So then I figure I have to delete the disk image. I pop in the live cd and navigate in nautilus as root to "/home/khalid/.VirtualBox/VDI" and delete (or so I believe)  the image. I try to log in again and can't. I go back to using the live cd and delete the contents of .trash under my home folder and in the root folder and it still doesnt do it. I finally get in after doing sudo apt-get clean. But now, when I check Disk Usage Analyzer and after deleting a whole bunch of stuff is says that 8.3 GB are still being used by the filesystem but / is only 3.8 GB. So, my question is, if they aren't under / where the hell are these 5 GB worth of pesky phantom files?? Thanks

---

### Post by theonlykman on 2007-10-14
Nevermind, it got sent to /.trash-root...and once I deleted it from there I had to delete it from /root/.Trash. Thats a little annoying...

---

