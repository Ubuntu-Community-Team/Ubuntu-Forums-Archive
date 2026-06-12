---
title: "Ubuntu sees my NTFS drives as RAID components.  I don't use RAID"
date: 2010-05-17
forum: Hardware
---

### Post by isuzudave on 2010-05-17
I am having a problem getting my NTFS formatted drives mounted when connected to the motherboard via SATA.  
	I have three hard drives connected to my motherboard.  One is a 250 GB IDE drive with Ubuntu 10.04.  The other two are identical Wester Digital 750 GB SATA drives .  One of the the 750 GB SATA drives has a NTFS Windows 7 install on one partition and two other NTFS data partitions.  The other 750 GB STAT drive is one NTFS partition used for video files.
	I dual boot between Windows 7 64 bit and Ubuntu 10.04 64 bit with no problems.  When I am in Ubuntu and go to the disk utility under system, administration, my NTFS drives show up, but it says they are part of a raid component, and I don't have an option to mount them.
	I have removed the 750 GB SATA drive that I use for video files and put it in a USB enclosure.  Ubuntu then sees the drives and mounts them with no problem.  It seems to only have a problem when they are both connected to my motherboard via SATA.  Does it assume that because they are the same model drive that I am using RAID?  Any suggestions?

---

### Post by isuzudave on 2010-05-20
Anyone?  This is driving me crazy.  Is there another area of the forums I should post this?  Should I report it as a bug?

---

### Post by theozzlives on 2010-05-20
Check to see if you have RAID setup in the BIOS.

---

### Post by isuzudave on 2010-05-21
> **theozzlives said:**
> Check to see if you have RAID setup in the BIOS.

Yep, I checked that.  I also tried with AHCI turned off/on and SATA port native mode disabled/enabled.

I also removed NTFS Configuration Tool in the Ubuntu software center, and installed mountmanager.  Mountmanager shows both of my SATA drives as isw_raid_member and I can not mount them.

I think it's a bug.

---

### Post by prismra on 2010-05-21
I have the exact same problem with my 1TB drive.  Is there a solution for this?

---

### Post by isuzudave on 2010-07-04
Anyone else have this problem?  I am still looking for a fix.

---

### Post by oldfred on 2010-07-04
Drives seem to save some raid meta data. Do not run this if you have RAID.

Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
Also check BIOS for raid settings
More discusion:
[http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738](http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738)

---

### Post by isuzudave on 2010-07-05
> **oldfred said:**
> Drives seem to save some raid meta data. Do not run this if you have RAID.

Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
Also check BIOS for raid settings
More discusion:
[http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738](http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738)

This seems to have fixed it.  Thank you so much.

---

