---
title: "Setting up Western Digital External Hard Drive"
date: 2008-08-31
forum: General Help
---

### Post by JockVSJock on 2008-08-31
Hey guys, I'm running Ubuntu 7.04 and have bought a external Western Digital External Hard Drive as a backup solution to backup my home directory on a daily basis via a cron job. 

The question I have is what would be the best file system to format the external hard drive?  Should I use vfat, which is how it is automatically recognized by the OS, or should I format it with ext3? 

I have some pretty large files (over 6GB) that I want to backup and don't want any surprises if the main drives fails.  I believe that vfat/fat32 has a limitation of 4GB: 

[http://en.wikipedia.org/wiki/File_Allocation_Table](http://en.wikipedia.org/wiki/File_Allocation_Table) 

Of course, I might have to connect this portable HD to Windows machines, and could either do all vfat or create a partition for vfat/fat32.  

Checking out info on ext3, looks like its limitation is 2Tib, probably a better choice: 

[http://en.wikipedia.org/wiki/Tebibyte](http://en.wikipedia.org/wiki/Tebibyte)

What would people recommend? 

thanks

---

### Post by Sycron on 2008-08-31
I would recomend ReiserFS or ext3. You can see the ext3 partition in Windows with *ext2 ifs* [http://www.fs-driver.org/](http://www.fs-driver.org/) .

---

### Post by JockVSJock on 2008-08-31
Cool, thanks!

---

