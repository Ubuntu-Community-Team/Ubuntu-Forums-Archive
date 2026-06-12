---
title: "[SOLVED] Partitioning for upgrade (+4 partitions?)"
date: 2008-12-29
forum: Installation &amp; Upgrades
---

### Post by sexyclient on 2008-12-29
I'm having some problems trying to partition my HD properly so that I can 1)upgrade without any major headaches and 2)streamline things most efficiently.  Here's my setup:

(gotten from gparted)
/dev/sda1 ntfs - 6.01 GB - windows backup partition (for rebooting)
/dev/sda2 ntfs - 17 GB - windows partition ("C:\" drive, and it has boot flag)
--unallocated - 147.91 GB--
/dev/sda3 - 2.03 GB - linux swap (ext3?)
/dev/sda4 ext3 - 16.98 GB - Ubuntu 8.04 Partition

I just resized my windows ntfs partition because I thought I could just make another partition (ntfs or ext3, I haven't decided which yet) to store data, but that was before I knew you couldn't have more than 4 main partitions on a drive.  I searched and read there was a way around this (I forgot, but it was something along the lines of making a "sub-partition" or something of that nature) but I couldn't find out how to do this.  I want to keep my home drive, update to the latest Ubuntu, and then use the new partition as my home directory - or something like that.  Can someone give me a helping hand?

---

### Post by Partyboi2 on 2008-12-29
Use gparted and delete your /swap partition and then create a extended partition using the unallocated space, then re-create your swap partition under the extended partition. Then you can create another partition or partitions under the extended partition  for storage or for what ever.

---

### Post by sexyclient on 2008-12-29
You rock so hard.  Thanks!
Is there a way to get ubuntu to display the mounted partition's name?  Other than having it display as "<filesize> GB Media"?  I used a gui tool (sorry, I forgot the name) to mount it automatically on startup as /media/data/ , but ubuntu still displays it by it's filesize.  Can I change this behavior?

---

### Post by Partyboi2 on 2008-12-29
Use gparted and right click on the partition you want to change name and select "Label" then change it to what ever you like. Then apply.

---

### Post by sexyclient on 2008-12-29
I don't have that option when I right-click on it.  I have the following choices:
*GREYED*(New)
-Delete
-Resize/Move
-Copy
*Greyed*(Paste)
-Format to > blah blah
-Mount on > /media/data
-Manage Flags
-Check
-Information

I'm using 8.04, could it be that I need a newer version of GParted?  Or maybe I'm just missing something completely obvious...

---

### Post by Partyboi2 on 2008-12-29
You could try doing it through the terminal
[https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive) 
Or you can try downloading [[COLOR=Blue]gparted[/COLOR]]("http://gparted.sourceforge.net/livecd.php") from there site

---

### Post by sexyclient on 2008-12-30
Sweet, I'm going to get GParted from the site - thanks again for all your help!

---

