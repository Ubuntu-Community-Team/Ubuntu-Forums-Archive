---
title: "Deleted partition, need to recover data"
date: 2007-04-06
forum: Hardware &amp; Laptops
---

### Post by alias320 on 2007-04-06
Hello-

I need help.  I have 160gig hardrive that has (had) 80gb ext3 for linux, 8 gig swap, and three 32gig fat32 partions to use between another drive that had XP on it.  I recently got an intel macbook, and wanted to use the harddrive with the mac as an external (i purchased one of those usb adapters for it).  I used it in the mac, but then I went to use the disk utility to delete a fat32 partition to make it a mac native one (dont ask me why, as this was a useless task).  The mac assured me that it would only affect the partition in question, and nothing else.  however it gave me an error and somewhere in the process seemed to delete the entire partition table on the drive.  when i put the drive back into the desktop, it cannot be read.  I used the live cd to see what gparted had to say, and it views the disk as without any partitions.  I downloaded testdisk on the livecd, however, since i cannot mount the drive, it cannot check the partitions.  There is of course valuable data to me on the currently inaccessible partitions that I would like to have back.  Is there anyway to either pull the data off the drive without a partition or restore the partitions long enough for me to pull the critical files off of it?  Thanks!

---

### Post by Higgo on 2007-04-07
This how to on TestDisk might help you:

[http://ubuntuforums.org/showthread.php?t=387922](http://ubuntuforums.org/showthread.php?t=387922)


Good luck

---

### Post by alias320 on 2007-04-07
i have testdisk running per the instructions in that post, however how do i actually recover the files.  I can see the files i want to recover, but dont know how to actually get them back.  Thanks!

---

### Post by alias320 on 2007-04-07
never mind- i couldnt copy since i wasnt using an NTFS partition.  I was however able to restore the partitions, so i was able to get my data off that way.  Thanks!

---

