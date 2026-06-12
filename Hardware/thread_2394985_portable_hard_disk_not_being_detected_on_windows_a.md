---
title: "portable hard disk not being detected on windows after using it in ubuntu 16.04"
date: 2018-06-24
forum: Hardware
---

### Post by a.sett on 2018-06-24
I used my external harddrive in an ubuntu 16.04 based system.
I am predominantly a windows user, and so on reconnecting it to my windows based system, the drive is simply not detected.
I thought that it may be that my drive is malfunctioning only on my pc, but its the same for any windows based system. 
It only works in Ubuntu based systems. 
How do i recover the data in my portable harddisk as there are to many important files in there. I cannot afford to format it up.

---

### Post by Autodave on 2018-06-25
How did you format the drive? Ext4?  If so, Windows will not read that. And, you will need to connect it to a Linux system to read and copy the files from it.

If you need to use an external drive on both Win and Linux, it is best to format it to NTFS.

---

### Post by yancek on 2018-06-25
The link below gives several methods which may work to do this by installing third party software.  As pointed out above, a default windows install will not read a Linux filesystem.  I've not used any of this software so have no idea if it works or works well.

[https://www.howtogeek.com/112888/3-ways-to-access-your-linux-partitions-from-windows/](https://www.howtogeek.com/112888/3-ways-to-access-your-linux-partitions-from-windows/)

---

