---
title: "Ubuntu shuts down during LVPM transfer"
date: 2009-04-27
forum: Installation &amp; Upgrades
---

### Post by djokela1 on 2009-04-27
Hi,

I originally installed Ubuntu with Wubi, and now am trying to move Ubuntu to its own partition so I can remove Windows. I have created an 15 GB ext3 partition for Ubuntu. But about 10-15 minutes after LVPM begins copying the files to that partition, the screen goes black, the graphical Ubuntu shut down screen appears, and the system shuts down. 

Something tells me that this is not supposed to happen. When I checked GParted, only 3.75 GB of data had been transfered to that new partition (sda2). When I checked the c:/ubuntu folder in Windows XP, it contained about 14.5 GB of data. I'm guessing (perhaps incorrectly) that this should be the size of the content transferred to the new partition.

Can someone tell me if this automatic shut down is typical? If not, any suggestions on how to make the transfer run completely? If it is notmal, how can I make sure all the files were copied from the NTFS (Windows) partition to the ext3 partition, so that I can delete the NTFS partition? 

I'm running Ubuntu 9.04 on a Gateway laptop with 1 GB ram (not sure what other specs you need...). 

Thanks a lot!

---

