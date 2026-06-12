---
title: "How to keeping data with install fresh Ubuntu?"
date: 2009-09-08
forum: Installation &amp; Upgrades
---

### Post by saidbakr on 2009-09-08
Hello,

In Windows I used to partition my hard disk into two - or more - partitions, one of them - the C partition - is dedicated to the OS - Windows Folder, Program Files - while the other is dedicated for data files - Images, documents, movies, games, etc.. -.

In the above situation when I decide to install fresh copy of windows, I just have to format the partition C only and therefore the other partitions are kept without data loss.

In Ubuntu, How could I able to do some thing similar to what I have described with Windows?

*By the way, I run Windows and Ubuntu on the same machine and Grub is used to maintain dual boot. The Ubuntu is installed over Small 8 G.B Hard disk - which is secondary master - while Windows is installed over Larger hard disk 80 G.B - which is Primary master -.*

---

### Post by Fafler on 2009-09-08
One partition for / and one for /home.

---

### Post by presence1960 on 2009-09-08
> **saidbakr said:**
> Hello,

In Windows I used to partition my hard disk into two - or more - partitions, one of them - the C partition - is dedicated to the OS - Windows Folder, Program Files - while the other is dedicated for data files - Images, documents, movies, games, etc.. -.

In the above situation when I decide to install fresh copy of windows, I just have to format the partition C only and therefore the other partitions are kept without data loss.

In Ubuntu, How could I able to do some thing similar to what I have described with Windows?

*By the way, I run Windows and Ubuntu on the same machine and Grub is used to maintain dual boot. The Ubuntu is installed over Small 8 G.B Hard disk - which is secondary master - while Windows is installed over Larger hard disk 80 G.B - which is Primary master -.*

You can create a separate /home partition when you install Ubuntu by choosing the manual (advanced) option at the prepare disk space (window 4 of 8). If you already have Ubuntu installed you can use gparted to create a new data partition (ext3). 

In either case when you do a clean install those partitions will remain untouched. In case of the /home partition you must highlight it during the install , click edit and set parameters: Use as : filesystem ext 3, **leave the format box unticked** set mount point on the drop down box  as /home. When all partitions are setup then continue with install.

I used to create a separate /home partition but got away from that opting to use a ext 3 data partition and use rsync to back up my home directory. For me that gives me more flexibility.

P.S. it will work whether you dual boot, only have Ubuntu or multiboot. I run Ubuntu 9.04, Sabayon 4.1, CrunchBang 9.04 & Windows.

---

### Post by saidbakr on 2009-09-08
> **presence1960 said:**
> You can create a separate /home partition when you install Ubuntu by choosing the manual (advanced) option at the prepare disk space (window 4 of 8). If you already have Ubuntu installed you can use gparted to create a new data partition (ext3). 

In either case when you do a clean install those partitions will remain untouched. In case of the /home partition you must highlight it during the install , click edit and set parameters: Use as : filesystem ext 3, **leave the format box unticked** set mount point on the drop down box  as /home. When all partitions are setup then continue with install.

I used to create a separate /home partition but got away from that opting to use a ext 3 data partition and use rsync to back up my home directory. For me that gives me more flexibility.

P.S. it will work whether you dual boot, only have Ubuntu or multiboot. I run Ubuntu 9.04, Sabayon 4.1, CrunchBang 9.04 & Windows.

Thank you for your detailed answer. I'm still a baby in the world of Linux, because I try to get a VISA to leave Windows world which I was born in it! I noticed something about this during installation of Ubuntu - mount point - but my fear of get loss my current computer life - Windows - pushed me to keep everything without advanced option.

I will be very appreciated, if you could able to tell me about some online resources that talk about Ubuntu file system and hard disk partitions in comparison with Windows.

---

### Post by presence1960 on 2009-09-08
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

[http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm)

[http://www.ubuntupocketguide.com/](http://www.ubuntupocketguide.com/)  -for a good step by step how to on installing ubuntu as well as many other topics

[http://en.wikipedia.org/wiki/Comparison_of_file_systems](http://en.wikipedia.org/wiki/Comparison_of_file_systems)

[http://www.freeos.com/articles/3102/](http://www.freeos.com/articles/3102/) some explanation of linux filesystem structure

[http://www.linux.org/lessons/advanced/x1254.html](http://www.linux.org/lessons/advanced/x1254.html) -more about linux filesystems ext2, ext3, etc

That is just for starters. if you do a google search of Linux filesystems you will get a good amount of hits

---

### Post by saidbakr on 2009-09-08
Thank you again!

---

