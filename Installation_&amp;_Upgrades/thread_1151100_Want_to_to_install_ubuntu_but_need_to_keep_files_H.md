---
title: "Want to to install ubuntu but need to keep files? HELP"
date: 2009-05-06
forum: Installation &amp; Upgrades
---

### Post by Redtwinky on 2009-05-06
:( I would like to install ubuntu, but I have a load of important files on vista...is there anyway I can keep all my files (Or as much files I can) while installing ubuntu. :)

---

### Post by lvleph on 2009-05-06
What I did was make a seperate NTFS partition, then moved My Documents to that parition. I believe you can do this by right clicking my documents and there should be a location that can be changed. Once all your document have been moved to the new ntfs partition you can then resize things and create a new Ubuntu partition. From there I created a symbolic link that pointed to My Documents on the NTFS partition. Now your docs are accessible from both OSes. If you are just going to move over to Ubuntu completely you can  Resize the Windows Partition and then browse to the My Documents location and then copy them to the Documents folder in your home folder. Then delete the windows partition and resize Ubuntu.

---

### Post by sgosnell on 2009-05-06
Whatever you do, make backups.  And backups of the backups, if the files are really important.  This applies even if you don't plan to change the OS.  Without backups, you will lose files.  Guaranteed, no matter what OS you have.  Murphy was an optimist.

With backups, you can do whatever you want with your OS and hard drive, and then restore the files you need from your backups.

---

### Post by lovinglinux on 2009-05-06
> **lvleph said:**
> If you are just going to move over to Ubuntu completely you can  Resize the Windows Partition and then browse to the My Documents location and then copy them to the Documents folder in your home folder. Then delete the windows partition and resize Ubuntu.

Why not create a new partition, copy the documents there and install Ubuntu over the Windows partition? Simpler, isn't it?

---

### Post by sgosnell on 2009-05-06
That would work, but making a copy on a completely different medium or disk, then restoring that backup, is easier and safer.  He needs the backup anyway, and it's possible to buy large USB HDDs for very little money these days.  If the data is too important to lose, then it must be backed up in different locations.  Copy to a HDD or flash drive, do whatever you want to the current HDD, and then copy back, keeping the copy in another location.

---

