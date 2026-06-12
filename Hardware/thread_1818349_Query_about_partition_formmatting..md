---
title: "Query about partition formmatting."
date: 2011-08-04
forum: Hardware
---

### Post by tylergard702 on 2011-08-04
Hello everyone,
I would like to ask a question about formatting hard drives.
I have an external 1.5TB hard drive that i need to change to FAT32 format, but have nothing big enough to back up the data already on it. I would like to ask if the 'change partition type' feature in Ubuntu's Disk Utility would keep the data on my hard drive, or erase it all like a normal format.
If not i will have to find another way to backup the data.
I apologise if this is in the wrong topic, it was the only one that fitted
Thank you in advance :).

---

### Post by gordintoronto on 2011-08-04
If you do anything to the partition, or format the drive, all your data will be lost. Perhaps you need to buy a second external drive. (That would let you have off-site backup, so your stuff would be OK even if your home has a catastrophe.)

---

### Post by oldfred on 2011-08-04
Reformats erase the data. I have heard of some tools that may convert from FAT to NTFS but anything of that type is very high risk and of course you have to have a good backup.

Why changing to FAT32? It is less reliable than NTFS or any Linux format. It will not hold a file over 4GB and will just truncate it without worning.

NTFS and Fat info:
FAT 4GB max & no journaling 
[http://technet.microsoft.com/en-us/library/cc938932.aspx](http://technet.microsoft.com/en-us/library/cc938932.aspx)
[http://technet.microsoft.com/en-us/library/cc940351.aspx](http://technet.microsoft.com/en-us/library/cc940351.aspx)
[http://www.ntfs.com/ntfs_vs_fat.htm](http://www.ntfs.com/ntfs_vs_fat.htm)

---

### Post by tylergard702 on 2011-08-05
Thank you for the answers :).
I wanted to use the hard drive as a media device for my PS3, however the PS3 is only compatible with FAT formats (unless hacked).
I have an 8GB memory stick that I can use instead, it's is just a pain to have to use the computer to transfer files before watching/playing on the PS3.
I gave the feature in Ubuntu's Disk Utility a try, and it didn't remove any data, however the PS3 still wouldn't read it and my computer wouldn't detect the hard drive when I plugged it back into my computer. It is working now though, I completely unplugged and therefore powered down the hard drive and when I plugged it back in it worked.
I guess I will have to use my memory stick for now until i find another method.
I would again like to thank everyone for the answers :D.

---

