---
title: "Breezy installer not recognizing partitions"
date: 2005-12-21
forum: Installation &amp; Upgrades
---

### Post by Birthdayboy on 2005-12-21
Hi there, 
My first post to this forum. And I have a problem. 
I want to install Breezy Badger on my laptop but when the installer comes to the point where I need to set the partitions for the install, it only recognizes the whole of my hard drive as one big free space. And yet I have 6 partitions on it. Three for Windows and three set up for Linux. Even when i try to manually edit edit the partition table, according to the documentation, it should list my partitions. But there is only the one big 30G "free space."
Does anybody have any idea why this is? PCLinuxOS and Suse all recognize my partitions but Breezy seems to fail at this... 
Any help is appreciated. 
Thanks

---

### Post by 23meg on 2005-12-21
Did you tweak your partitions with a Windows partitioning utility such as Partition Magic? What filesystems do you have on these partitions?

---

### Post by Birthdayboy on 2005-12-21
Hi 23meg
I have Acronis Disk Director 9 on my Windows XP Home system and with that I did partition my drive. I also did change the cluster size on my one NTFS partition from 4K to 2K with Acronis. Other than that I have not tweaked any partitions with Acronis. Two of my Windows partitons are NTFS and one is FAT32. My other partitions are one linux swap and two ReiserFS, all in preparation to install Ubuntu. In all I have six partitions.

---

### Post by roelofs on 2005-12-28
I had the exact same problem and would love to know what *should* have worked.  In the end I lost patience and blew away the entire extended partition, but that should not have been necessary.

Details available at [LinuxQuestions]("http://www.linuxquestions.org/questions/showthread.php?threadid=349241"), for what it's worth.  Original partitioning might have been done with a Maxtor utility.

---

### Post by halg on 2005-12-29
[QUOTE=Birthdayboy]Hi there, 
My first post to this forum. And I have a problem. 
I want to install Breezy Badger on my laptop but when the installer comes to the point where I need to set the partitions for the install, it only recognizes the whole of my hard drive as one big free space. And yet I have 6 partitions on it. Three for Windows and three set up for Linux. Even when i try to manually edit edit the partition table, according to the documentation, it should list my partitions. But there is only the one big 30G "free space."
Does anybody have any idea why this is? PCLinuxOS and Suse all recognize my partitions but Breezy seems to fail at this... 
Any help is appreciated. 
Thanks[/QUOTE]
 
Which version of SUSE *does* recognize your partitions?   Funny, I am having the exact same problem with SUSE 10.0 Personal:  It does not recognize existing partition tables.  Could be coincidental though.

I am just curious.  Got into a spat with a difficult moderator on the SUSE boards over this topic.  He did not seem to feel it warranted a "problem."  Hope that does not happen here.

---

### Post by az on 2005-12-29
The only time I have seen this happen is when you use a linux tool to create some partitions and then use a windows tool to modify the partition table.  Windows tools seem to enjoy screwing up the partiton table when there are non-windows partitions on it.

That would be just about the only time the Ubuntu installer gets confused about the partitiong table.

I have never done this, but you can blow away about fifteen minutes of work (and possibly all your data) by clobbering the partition table with fdisk and then running parted from the installer and try rescuing your partitions.  Parted will look where you tell it to look for partitions and create the appropriate entries into the partition table.

Perhaps there is a more elegant way to redo one's partition table?

---

