---
title: "Dual Boot: Alternate Partition Access"
date: 2005-10-09
forum: Hardware &amp; Laptops
---

### Post by Pitbull11188 on 2005-10-09
I have a dual boot system set up and I want to move my music between the partitions from WInXP->Breezy Linux. I have heard that it is impossible to access ntfs partitions from linux but there has to be some way to transfer files betwixt the two. Any ideas?

---

### Post by darkmatter on 2005-10-09
[QUOTE=Pitbull11188]I have a dual boot system set up and I want to move my music between the partitions from WInXP->Breezy Linux. I have heard that it is impossible to access ntfs partitions from linux but there has to be some way to transfer files betwixt the two. Any ideas?[/QUOTE]

It is possible to mount NTFS, but as read only (you can import to Linux, but cannot write to NTFS).

If you want to be able to share data between both OS's, you will need to create a third partition as FAT 32. Since both Linux and Windows have read/write access to a FAT partition, this third partition will act as a middle-man, allowing you to transfer data between the two if you wish.

An added benefit to this setup is, as both Windows and Linux can read from it, that you can use the FAT partition as storage for your music, pictures,etc.

That way you can just point your applications to the appropriate folders/files on the FAT partition. You don't need to transfer files between the OS's. It saves time/work and reduces the chances of duplicate entries.

---

### Post by casper_2095 on 2005-10-10
If you just want to listen to your music files then mounting the ntfs partition is the most straightforward way.  For example (from memory) where /dev/hda3 is the fourth partition on the first ide drive...
```

$ man mount
$ mount -t ntfs -o ro /dev/hda3 /mnt
```

If you want to copy those files to another partition (like an ext3 - or "linux" partition) then mount the ntfs partition as above and cp the files from one to the other.  For example to copy stuff from the above mounted drive to your home directory...
```

$ man cp
$ cp -r -p /mnt/mymusic /home/dude/music
```
-r = recursive (all the subfolders also)
-p = preserve (don't change the timestamps)

Copying from one partition to another on the same disk can take a while.

---

