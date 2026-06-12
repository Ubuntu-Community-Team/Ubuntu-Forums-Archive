---
title: "Partitioning assistance"
date: 2008-10-13
forum: General Help
---

### Post by devosion on 2008-10-13
I have recently decided to dual boot Ubuntu and Vista, mostly so I can play the games that I havent played in about a year since I decided to devote my time learning ubuntu. In any case I will be following a dual boot process for the most part but I also wanted to set up a third partition for back-up and various media. How would I go about setting this up with three hard drives? I currently have one hard drive devoted to ubuntu (120gb with / and /home using ext3), an ide hard drive im having problems with (60gb with Vista using ntfs or fat32, could use a recommendation on the file system), and the third hard drive that will be for backup and media purposes (500gb and maybe /multimedia using ext3). How can I set this up effectively and properly?

---

### Post by Washer on 2008-10-14
I'd personally go with ntfs on windows &  all OS's on one drive.

---

### Post by Liviu-Theodor on 2008-10-14
I will reccomend: first install Vista, than Ubuntu. But it is better (safer) to disconnect the Ubuntu HDD for the Vista install, and the Vista HDD for the Ubuntu install. For the Ubuntu partitions, use ext3, for the Vista partitions, use NTFS. For the common partitions, use ntfs (better), or fat32. While I haven't encountered any problem with ubuntu reading or writing ntfs drives (I know of at least one case where Windows, but XP, not Vista, was installed on a ntfs partition formatted under Ubuntu, with GParted). And for further information about installing a dual-boot, read [http://www.psychocats.net/ubuntu/index]("http://www.psychocats.net/ubuntu/index").

---

### Post by bigbrovar on 2008-10-14
follow this guides i created a while back 
[http://ubuntuforums.org/showpost.php?p=5045657&postcount=5](http://ubuntuforums.org/showpost.php?p=5045657&postcount=5)

[http://ubuntuforums.org/showpost.php?p=5046302&postcount=14](http://ubuntuforums.org/showpost.php?p=5046302&postcount=14)

---

