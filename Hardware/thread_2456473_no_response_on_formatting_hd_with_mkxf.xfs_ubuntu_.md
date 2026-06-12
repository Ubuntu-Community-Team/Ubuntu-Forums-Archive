---
title: "no response on formatting hd with mkxf.xfs ubuntu 20.04"
date: 2021-01-12
forum: Hardware
---

### Post by dieter-erich on 2021-01-12
Hi,
   I formatted a 16 TB disk to ext4 and everything worked fine. However, when writing onto the disk I run out of inodes because of a very big number of files. I thus decided to re-format it to xfs. I unmounted the disk, checked with lsblk that it was indeed /dev/sdf and finally I run:
sudo mkfs.xfs -f -L XFS -b size=1024 /dev/sdf

but nothing happend. I did not get any message on the progress of formatting nor any other output. 
The terminal I had started it from was unresponsive to everything including <ctrl c>. I closed it but still found mkfs-related processes with
"ps -ealf|grep mkfs.xfs. However, these could not be killed. 
gparted gets stuck as well presumably because of the incorrectly formatted disk. I cannot reboot because I have something important running.... 

How can I get control of the disk again?
thanks, best, D-E

---

### Post by The Cog on 2021-01-12
16TB is quite big. I don't know XFS, but is it possible that mkfs.xfs was still busy writing to the disk? "iostat -x 2" should show you if the disk is being actively used. Not being killable might indicate that those processes were stuck in an I/O call waiting for disk writes to complete. Just guessing.

---

### Post by dieter-erich on 2021-01-12
Thank you! The formatting was run over night, I believe that 7 hrs should do. iostat -x 2 does not show any activity on this disk. What else could I try?

---

### Post by dieter-erich on 2021-01-12
SOLVED: disconnecting/reconnecting the disk brought it back to life. Fortunately, I found somebody at the place to do it!

---

