---
title: "slow gparted"
date: 2009-04-14
forum: Installation &amp; Upgrades
---

### Post by zwygart on 2009-04-14
Hello everybody,

I want to know why gparted is so slow on on jaunty (9.04).

I copied the ISO on to a USB key, boot from there and wanted to partition the home computer to install jaunty. The computer is a HP Pavilion, 3GHz, 512Mb of RAM. First disk has XP (NTFS) and a FAT32 partition, total 160G. The second disk is 320G with boot partition, extended with hardy, intrepid and 2 swaps, followed by a fat32 for backup and a ext home partition. My USB key has 13 fat followed by 2 900Mb ext3. 

What happens is that the first disk it took like 30s, the second more than 5min to scan, so unable to use it efficiently. When I closed Gparted it remains a process dosfsck or something. When I start gparted from my installed hardy, it scans all the drives in less than 5 seconds. 

Why is gparted so slow from Live? Or should I be more patient?

I"m writing this from LiveUSB 9.04 and it works well. 

Thanks for any advice.

---

### Post by zwygart on 2009-04-21
Hi everybody,

Since nobody answered I have tried some thing. May be it will happen to somebody else, so here is how I did : 

I waited until it was working on sdb during 15 minutes( not necessary to be as long).
Then go in a terminal and type "top". This will show wich process is using what. System Monitor don"t display all process. 
Check the PID of dosfsck, wich should use the most CPU. 
Quit by pressing q.
Type "kill " followed by the PID.

This happened in finishing scanning very fast. But a Attention mark was putted to the partition. Since I don"t need to do anything with it, I don"t carried, and all went smooth (partitionning and installing jaunty).

---

