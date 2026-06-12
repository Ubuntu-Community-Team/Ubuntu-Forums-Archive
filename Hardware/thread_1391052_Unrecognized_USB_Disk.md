---
title: "Unrecognized USB Disk"
date: 2010-01-26
forum: Hardware
---

### Post by pjc007 on 2010-01-26
Hi Folks,
 
I have a strange problem that has just started occurring, where one of two external drives is not being recognized/automatically mounted.
 
Hardware:
 
Acer Aspire 5715Z
External Maxtor 360GB USB Drive
External Toshiba 1TB USB Drive
 
Software:
 
Dual-boot Windows 7/Ubuntu Lucid
 
The Maxtor is automatically mounted and appears correctly in /media/Storage1
The Toshiba is not recognized or mounted.
 
Running Disk Utility in Ubuntu shows the Toshiba drive as a 1TB drive, with a 1TB NTFS partition, but no Partition info (no name, etc).
 
I can manually mount the Toshiba drive with:
 
mount -t ntfs /dev/sdc1 /mnt/Toshiba
 
Both the Maxtor and Toshiba are working just fine under "Windows 7", and a Win 7 disk check reveals no problems on the Toshiba.
 
Any ideas why suddenly, one is showing up correctly and the other isn't?
 
Note - this configuration was working previously (with lucid)...
 
Thanks in advance!
 
-PJC

---

