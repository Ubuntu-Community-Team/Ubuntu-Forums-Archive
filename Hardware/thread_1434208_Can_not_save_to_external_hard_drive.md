---
title: "Can not save to external hard drive"
date: 2010-03-20
forum: Hardware
---

### Post by Segwagwa on 2010-03-20
I have a WD My password essential external hard drive.  In Windows xp,  vistan and 7 I can use it fine, however, my Ubuntu (9.10) can not save to it.  I  keep getting the message "error while copying to WD Smartware,  destination is read only".  I have tried formating to NTFS, Fat 32,  using G-parted (which sees all partitions on my machine expect this  external hard drive).  How can I get this silly thing to work.  I have  used other external hard drives with out a problem and my memory  stick (flash disks) work fine. Ps: it comes with pre-loaded software to  back up system (that only works for windows) even though I have  formatted it the software is not deleted. Go easy I am new to this

---

### Post by Goveynetcom on 2010-03-20
> **Segwagwa said:**
> I have a WD My password essential external hard drive.  In Windows xp,  vistan and 7 I can use it fine, however, my Ubuntu (9.10) can not save to it.  I  keep getting the message "error while copying to WD Smartware,  destination is read only".  I have tried formating to NTFS, Fat 32,  using G-parted (which sees all partitions on my machine expect this  external hard drive).  How can I get this silly thing to work.  I have  used other external hard drives with out a problem and my memory  stick (flash disks) work fine. Ps: it comes with pre-loaded software to  back up system (that only works for windows) even though I have  formatted it the software is not deleted. Go easy I am new to this
I have had these problems before (different device, but still removable media), and I can't remember exactly how I fixed it. I believe I just reformatted it to FAT32 in Windows XP, and when I reconnected it, all the software was gone, and it allowed me to write to it. Also, FYI NTFS is sorta a bad thing to do for Linux, I have many troubles with NTFS in Linux (as have others), if you do get it fixed, I recommend formatting it to ext3 or the better ext4 (which supports file sizes up to 16 TiB) for Linux (it won't be cross compatible but it will work great for Linux).

Update, on any new status...

---

### Post by Segwagwa on 2010-03-20
Thanks I have tried formating in XP as well but did not help.  I do need the hard drive to be able to work both in Windows and Linux.

---

### Post by HoodedHooligan on 2010-04-09
I have the exact same problem except I have I no longer have excess to any form of Windows. My external has all my stuff on it and I can't get to any of it through Ubuntu 9.10

---

### Post by ramsonite on 2010-07-21
> **Segwagwa said:**
> I have a WD My password essential external hard drive.  In Windows xp,  vistan and 7 I can use it fine, however, my Ubuntu (9.10) can not save to it.  I  keep getting the message "error while copying to WD Smartware,  destination is read only".  I have tried formating to NTFS, Fat 32,  using G-parted (which sees all partitions on my machine expect this  external hard drive).  How can I get this silly thing to work.  I have  used other external hard drives with out a problem and my memory  stick (flash disks) work fine. Ps: it comes with pre-loaded software to  back up system (that only works for windows) even though I have  formatted it the software is not deleted. Go easy I am new to this


Segwagwa: have you had any success on your problem?? I have exactly the same problem with the same WD "My Passport" ext hard drive, and I cant seem to find a solution through this forum. 
Please if you had it worked out let me know!!

---

