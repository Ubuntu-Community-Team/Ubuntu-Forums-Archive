---
title: "Ubuntu RAID help"
date: 2007-06-25
forum: Hardware &amp; Laptops
---

### Post by Havek on 2007-06-25
I am new to Ubuntu and i am trying to install it on my RAID 1 i have windows on.  I tried walking through the FakeRaidHowto but got the error "No RAID disks",  So in trying the solve i can to a stopping point.  Sorry i tried several times but could not seem to put this output in a .tar.  So i am just going to cut and paste.

Here is what is said:

ubuntu@ubuntu:~$ sudo fdisk -u -l /dev/sda

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   312560639   156280288+   7  HPFS/NTFS

After entering the dd f=/devsda/...

ubuntu@ubuntu:~$ sudo dd if=/dev/sda of=outputfile skip=312579808
2000+0 records in
2000+0 records out
1024000 bytes (1.0 MB) copied, 0.0792119 seconds, 12.9 MB/s

Is there anyway i can get this Fake Raid to work?

---

