---
title: "How to have a FAT32 partition mounted automatically?"
date: 2016-01-27
forum: Hardware
---

### Post by TBK on 2016-01-27
I'm using Ubuntu 15.10.
I have used this method to solve this problem:
1. Make a new folder have name "TBKDATA" in /media/
2. gksu gedit /etc/fstab (terminal)
3. Add this line to the end of the file: UUID=D955-BE70 /media/TBKDATA vfat defaults,utf8,umask=000 0 2
4. sudo mount -a (terminal)

But with this method, I can't edit permissions this partition or files/folder inside it for each other account, I also have tried to do this with nautilus/nemo as root.
How to solve this problem?

---

### Post by oldfred on 2016-01-27
FAT & NTFS have no ownership nor permissions, as they are Windows formats.
So only the defaults you set when mounting are used.

Generally better to use NTFS as FAT32 cannot have a file larger than 4GB nor does it have a journal, so repairs can take longer. FAT32 is ok for small partitions like an ESP - efi system partition or smaller flash drives.

 Older systems with older version of NTFS-3g: 
Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
HOWTO: Mount NTFS partitions with specific ownership/permissions - WorMzy
[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)

---

