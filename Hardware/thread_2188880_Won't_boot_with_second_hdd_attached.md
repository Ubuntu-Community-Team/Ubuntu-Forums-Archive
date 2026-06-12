---
title: "Won't boot with second hdd attached"
date: 2013-11-19
forum: Hardware
---

### Post by starving030 on 2013-11-19
I'm running Ubuntu 10.04. All of a sudden if I try to boot with any other storage attached I get an error message. It does it with two different hdd's and all three of my thumb drives. If i disconnect everything but the main drive it works fine. Also, I dual boot XP and it boots up fine.
> ALERT! /host/ubuntu/disks/root.disk does not exist. Dropping to a shell!
Any ideas?

Thanks

---

### Post by oldfred on 2013-11-19
/host indicated you have wubi?
The 10.04 version desktop is not supported although server version will be supported for a while.
And wubi 12.04 is the last fully supported versioin of wubi.

Does Windows need chkdsk? And wubi fsck? 
 [http://ubuntu-with-wubi.blogspot.ca/2011/08/missing-rootdisk.html](http://ubuntu-with-wubi.blogspot.ca/2011/08/missing-rootdisk.html)

But not sure how that might cause that type of issue as generally BIOS determined drives and then operating system uses BIOS info for its drive info.

 Wubi not available with 13.04
[https://lists.ubuntu.com/archives/ubuntu-devel/2013-April/036993.html](https://lists.ubuntu.com/archives/ubuntu-devel/2013-April/036993.html)

      
 [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

      
 From the developer of wubi:
[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)
Agostino: Wubi actually wasn&#8217;t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.

---

### Post by starving030 on 2013-11-20
> **oldfred said:**
> /host indicated you have wubi?
The 10.04 version desktop is not supported although server version will be supported for a while.
And wubi 12.04 is the last fully supported versioin of wubi.
I'm sorry. I am quite ignorant when it comes to this stuff. I am confused with most of that that you wrote, not sure what Wubi even is or does. I looked in */host* and there were two files that resembled the term "Wubi". They were "Wubildr" and "Wubildr.mbr". Is that what you were asking?

---

### Post by oldfred on 2013-11-20
Review the links posted.

Wubi is a version of Ubuntu intended for Windows users who want to try Ubuntu without repartitioning. It uses the Windows boot loader and is just a file inside the Windows NTFS partition. It has a max file size of 30GB. But since it is running inside the NTFS partition it relies on Windows working and is not intended for long term use.

---

### Post by starving030 on 2013-11-26
so do I delete or rename the file or something so it doesn't use it? What should I do?

---

### Post by oldfred on 2013-11-26
if you like and use Ubuntu, it is time to update to separate partitions. 

       This does require you to create partitions to convert install into. You can also just fully backup /home and create a list of installed apps. Then do a new install and restore your /home and add back the apps.
I tend to prefer new clean installs over upgrades, especially when a LTS to LTS install.

 HOWTO: migrate wubi install to partition - bcbc 
[https://help.ubuntu.com/community/MigrateWubi](https://help.ubuntu.com/community/MigrateWubi)
[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)
[https://wiki.ubuntu.com/WubiGuide#How_do_I_migrate_to_a_real_partition.2C_and.2BAC8-or_get_rid_of_Windows_entirely.3F](https://wiki.ubuntu.com/WubiGuide#How_do_I_migrate_to_a_real_partition.2C_and.2BAC8-or_get_rid_of_Windows_entirely.3F)

After migrating you still should do an upgrade to 12.04. 
      
 Basics of partitions:
[http://en.wikipedia.org/wiki/Disk_partitioning](http://en.wikipedia.org/wiki/Disk_partitioning)
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
[https://help.ubuntu.com/community/PartitioningSchemes](https://help.ubuntu.com/community/PartitioningSchemes)

With XP you can use gparted to also shrink the NTFS partition. All newer versions of Windows should use the Windows Disk tools to shrink Windows, but not create any new partitions.

 GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)
Partitioning basics with some info on /data, older but still good bodhi.zazen
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)

---

