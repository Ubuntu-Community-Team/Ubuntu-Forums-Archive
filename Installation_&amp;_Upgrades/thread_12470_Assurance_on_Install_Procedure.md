---
title: "Assurance on Install Procedure"
date: 2005-01-24
forum: Installation &amp; Upgrades
---

### Post by phend-one on 2005-01-24
Hi there, 

Just like to say this is the first time in these forums, although I have been lurking for a while.

My question is about the install procedure. I am currently running WindowsXP Pro, and have made ~4Gb of space free and formmated it into the FAT32 filesystem so that ubuntu will be able to detect it (not sure if this even matters). The rest of the partitions are in NTFS format.

When I begin to install ubuntu into the 4Gb partition, it should be smooth right? Will I need to create additional partitions within that one for swap, home and /?

After installation, will I be able to boot back into Windows XP at will (dual-boot)? And which boot loader will be used? Is there a way to use XP's default one?

Thanks!
-phend.one

---

### Post by az on 2005-01-24
You will need to delete your 4 gig partition.  The, use guided partitionning for the free space.  That will make your swap and so forth.  You will need to change the default in grub to boot into windows XP by default.   By default, you will bootinto Ubuntu first and need to select Windows to boot into it.

---

### Post by phend-one on 2005-01-24
How do you delete the partition? Is there a option in the ubuntu install? Maybe another alternative than Partition Magic?

---

### Post by az on 2005-01-25
The installer will prompt you to use the entire disk.  Tell it to use manual partitioning.

Select the target partition
Tell it to delete.
Select guided partitioning.
That should automaticaly use the free space you just created.  Make sure (it will show you before it goes...)
Gidde up!

---

### Post by eldrich_rebello on 2005-01-25
just one question.is the "guided partitioning" thingy a work of the ubuntu developers or is this also available in debian sarge?

---

### Post by az on 2005-01-25
The Ubuntu installer is made from the Debian installer.  Warty's is based on the previous version of the current Sarge installer (RC2)

So, it is the same guided partitioning.

---

