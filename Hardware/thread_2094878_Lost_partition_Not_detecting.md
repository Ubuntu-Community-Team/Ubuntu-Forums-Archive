---
title: "Lost partition: Not detecting"
date: 2012-12-15
forum: Hardware
---

### Post by newbcat on 2012-12-15
Im running Ubuntu 11.10 from the USB stick. 
I have a 2TB internal HDD which has 2 partitions of 1 TB each.
Problem is that Ubuntu here is detecting only **one of the two** partitions.
I cant see the other partition in Gparted or in the 'Disk Utility' App.
Its kind of a lost partition which I want to bring back.
Please help me detect and mount it. :(
I hope all the data on other partition is safe. 

Thank you

---

### Post by oldfred on 2012-12-15
Does gparted show a little yellow or red icon that you can click and see what it says may be wrong with partition?

Are partitions NTFS and have you run chkdsk from a Windows system or if Linux e2fsck from your Ubuntu install?

---

### Post by Steve Francis on 2013-03-03
> **newbcat said:**
> Im running Ubuntu 11.10 from the USB stick. 
I have a 2TB internal HDD which has 2 partitions of 1 TB each.
Problem is that Ubuntu here is detecting only **one of the two** partitions.
I cant see the other partition in Gparted or in the 'Disk Utility' App.
Its kind of a lost partition which I want to bring back.
Please help me detect and mount it. :(
I hope all the data on other partition is safe. 

Thank you

I managed to solve a similar problem using TestDisk. As oldfred says, is your partition ntfs?

After a power supply interruption to my dual boot laptop, XP and Ubuntu would no longer recognise an extended NTFS partition containing all my precious data files. Initial attempts to recover just led to error messages reporting bad sectors.

I used the method described here
[http://html5.litten.com/how-to-fix-external-disk-drive-suddenly-became-raw/](http://html5.litten.com/how-to-fix-external-disk-drive-suddenly-became-raw/)
to retrieve them.

I should point out that two things were key for me:
1. In answer to the question "Should TestDisk search for partition created under Vista or later?", I had to answer "Y". If I answered "N", TestDisk would find the lost partition but that partition would not appear when rebooting into XP.
2. I had to use the XP CD-ROM to run Recovery Console and then run the command: chkdsk e: /r      
The chkdsk process took 14 hours! At the end of it though, I rebooted and XP recognised the partition and the files on it.

Needless to say, I immediately did a back up of the data files. ;)

---

