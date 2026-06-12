---
title: "How to view/manage ubuntu drive from windowsXP"
date: 2008-09-27
forum: General Help
---

### Post by sunshine12 on 2008-09-27
Hi,

I have to 2 OS, windows XP and ubuntu. From Ubuntu I can view/manage files from the windows XP drive (NTFS formatted) by default. But I can't see the drive where I installed Ubuntu from windowsXP.

Is there any software that allow me to view/manage files from windows to ubuntu?

Thanks

---

### Post by fooman on 2008-09-27
> **sunshine12 said:**
> 
Is there any software that allow me to view/manage files from windows to ubuntu?


yes,  there is (for ext2/ext3):

[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by sunshine12 on 2008-09-27
> **fooman said:**
> yes,  there is (for ext2/ext3):

[http://www.fs-driver.org/](http://www.fs-driver.org/)

Thanks a lot.

---

### Post by TeXtonyx on 2008-09-28
I had a choice between fs-driver and LinuxReader from Diskinternals, and chose Linux
Reader because there were a few reports of fs-driver corrupting the partition over time.
LinuxReader lets you read Ubuntu and copy files (extract) to XP but not write to Ubuntu.
You can install fs-driver in read only mode, but it also assigns drive letters to partitions.
One guy reported that XP had started monitoring the Ubuntu drive letter for system 
restore and he couldn't turn it off.

---

