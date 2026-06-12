---
title: "External HDD Mounts, But Files Cannot Be Seen"
date: 2010-12-16
forum: Hardware
---

### Post by mn102193 on 2010-12-16
Like the title says, my seagate freeagent goflex 320GB DOES mount on the desktop, but when I open it, there's nothing to be seen. But the disk space reflects that there are 29GB of data on the HDD. Thanks for any help!

---

### Post by bobcollard on 2010-12-16
> **mn102193 said:**
> Like the title says, my seagate freeagent goflex 320GB DOES mount on the desktop, but when I open it, there's nothing to be seen. But the disk space reflects that there are 29GB of data on the HDD. Thanks for any help!
Is it formatted FAT32?  If it is NTSF from a Mac you may need to install something to read that format.  You may benefit from reading this:
[http://en.wikipedia.org/wiki/Disk_formatting](http://en.wikipedia.org/wiki/Disk_formatting)

---

### Post by mn102193 on 2010-12-16
It's NTFS, and it has my music library on it which I had to save from Vista, which I installed Lucid over. I do still have access to a Windows comp if I need to do anything on that end.

---

### Post by mn102193 on 2010-12-17
bump. 
and to clarify, this HDD has music that was manually transferred to it. but the folders cannot be accessed from Ubuntu.

---

### Post by bobcollard on 2010-12-17
Thought so, look in your Synaptic Package Manager.  I found this that might help you:

---

### Post by efflandt on 2010-12-17
Do you always "safely remove" it when disconnecting it?  Normally a USB drive will auto mount, but that may not happen if a Windows file system is unclean, or other issues that make Linux not want to touch it until Windows fixes it.

You might try connecting it to a Windows computer, figure out what drive letter it is, and then do **chkdsk /f X:** (replace X with its actual drive letter) from a command window in Windows.  Then see if it works with Linux.

---

### Post by mn102193 on 2010-12-17
Once again, the drive does mount, but the files on the drive cannot be seen.
EDIT: now the drive won't mount, and i'm getting this: Unable to mount FreeAgent GoFlex Drive
Error mounting: mount exited with exit code 1: helper failed with:
mount: only root can mount /dev/sdf1 on /media/ 
FreeAgent GoFlex Drive

---

### Post by mn102193 on 2010-12-18
Fixed it. I had to put the files on a windows machine, reformat the HDD from NTFS to FAT32. Runs fine now.

---

