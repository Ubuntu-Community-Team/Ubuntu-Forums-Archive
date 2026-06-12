---
title: "Reinstalling Ubuntu in a dual boot system"
date: 2009-07-24
forum: Installation &amp; Upgrades
---

### Post by frs89 on 2009-07-24
Hi all,

I have Ubuntu 8.10 and winXP installed in dual boot on my laptop. It happens that I messed up the ubuntu and now it doesn't start, since I only used ubuntu for some programation I'm thinking to replace the old version for 9.04, but I'm afraid to erase my windows stuff as well.
 
Here's a link to my disk management on XP 
[http://img196.imageshack.us/img196/2061/printscr.jpg](http://img196.imageshack.us/img196/2061/printscr.jpg)

Is safe and efficient to erase partitions with disk management on windows?

If I erase the Ubuntu partion I would not be able to start winXP because of the bootloader, if I install the Ubuntu afterwards there will be no problems?

While installing Ubuntu what are the configurations that I have to choose?

I need some help please. I'm a newbie on Ubuntu and details are very important to me.

Thanks, 
Silvestre

---

### Post by LowSky on 2009-07-24
istall 9.04 to the old 8.10 patition, no it will not mess up windows from booting up as long as you choose the correct method of installing. dont use windows to erase linux partitions, use the Ubuntu Live CD its much better than windows at that job.

best option is to run the LiveCd, chose to install, whn you get to the part about partitioning, choose manual, no carefully reformate and label the linux partition with the mount point of /
 once done you will easily be dualbooting into windows and linux
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by frs89 on 2009-07-24
Thanks, I have some doubts still.. I have 4 partitions, PQservice, Windows, Linux, Swap (Linux), (I think is Swap, I'm correct?), the options are New, Edit and Delete (partition), what I'm suposed to do? Edit the Linux Partition and not touching the others? In Editing I have other options:
 -Use As..
 -Format
 -Mount Point
     
I have to change the SWAP or delete and create another one? With which parameters?

Thanks for the help.

---

