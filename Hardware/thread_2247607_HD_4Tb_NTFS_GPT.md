---
title: "HD 4Tb NTFS GPT"
date: 2014-10-09
forum: Hardware
---

### Post by restrel on 2014-10-09
hi all,

someone can tell me how can i configure  kubuntu in order to see (and use) a 4Tb internal hard disk  formatted under Windows7  in NTFS dinamic GPT ?

---

### Post by TheFu on 2014-10-09
Did you mount it or is there some other issue?

---

### Post by ajgreeny on 2014-10-09
> NTFS dinamic GPT ? 						Does this mean that the partition is a windows Dynamic filesystem.

If it is, you will have no luck as I don't think Linux can see nor use dynamic partitions, as discussed in this thread.
[http://ubuntuforums.org/showthread.php?t=2137683](http://ubuntuforums.org/showthread.php?t=2137683)

---

### Post by oldfred on 2014-10-09
Post these:

sudo parted -l

You may have to install gdisk, if you do not have it.
sudo apt-get install gdisk
 sudo gdisk -l /dev/sda

      
 GPT fdisk Tutorial - user srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)

Windows does do some strange things to large gpt drives and an older Windows version may be an issue.

---

