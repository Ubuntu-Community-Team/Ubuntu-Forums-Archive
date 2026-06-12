---
title: "Hard drive salvage software?"
date: 2008-08-01
forum: General Help
---

### Post by original_jamingrit on 2008-08-01
A have a friend with an external hard drive, RAID, probably NTFS.  He uses Ubuntu, and says that this hard drive doesn't seem to work with either Windows or Ubuntu.  using fdisk -l or cfdisk reports that it doesn't have a valid partition table, and I'm not able to mount it.  I'm all but convinced that his drive is ruined, and I was wondering if there is any other diagnosis tools or disklabel repair tools I need to be using?  (Preferably command line, as I'm helping him through ssh)

fdisk-l:```
$ sudo fdisk -l /dev/sdf

Disk /dev/sdf: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa8fc4a17

Disk /dev/sdf doesn't contain a valid partition table
```

any advice or suggestions would be great.

---

### Post by mkvnmtr on 2008-08-01
Don't think I can help but I seem to remember reading that Linux can't read that format. I did see a package that you can download that says it helps with the format but I don't remember what section. I don't use it so I didn't pay much attencion.

---

### Post by librarian on 2008-08-02
This might help: [URL https://help.ubuntu.com/community/DataRecovery?highlight=(CategoryBackupRecovery)]DataRecovery[/URL] from the Ubuntu community docs. You might also need to install ntfsprogs.

---

### Post by librarian on 2008-08-02
Let's try that link again - sorry...

> **librarian said:**
> This might help: [DataRecovery]("https://help.ubuntu.com/community/DataRecovery?highlight=(CategoryBackupRecovery)") from the Ubuntu community docs. You might also need to install ntfsprogs.

---

