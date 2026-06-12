---
title: "can not access/delete files: input/output error in Karmic"
date: 2009-12-29
forum: Hardware
---

### Post by bilol on 2009-12-29
Hello Everybody,
I am facing a serious problem while accessing some files from my external hard disk.
I have a dual boot machine with Windows XP and Ubuntu 9.10.While I was copying some files from my internal disk to the external partition /dev/sdb5 (having mount point /media/DisK3), the machine gets hanged.

After forcefully restarting the machine ubuntu was unable to mount /media/DisK3 and shows the error in the screen shot attached herewith.

I reboot the machine in windows and was able to access the partition /media/DisK3.However I was unable to access/delete some files stored in /media/DisK3.When I get back to Ubuntu,the partition is mounted,but the problem persists.While trying to access/delete these files the system yields "***input/output error***".Even I tried to delete those files by their inode numbers,acquiring the super user privilege; but everything was in vain.
This problem is not new to me.In the previous occurrence of this problem([previous thread]("http://ubuntuforums.org/showthread.php?t=1357398")),I took the important back up and format the disk entirely from Windows,in NTFS.Then the system worked fine.However in this occasion,I do not want to format the disk, because of two reasons:(i)There is no guarantee that the problem will not occur soon (ii)Right now,I do not have sufficient space to take the total backup.
So,please help me......Tell me some ways to delete those files *without reformatting*......
Thanks in anticipation.

---

### Post by bilol on 2009-12-31
Is there any solution?????

---

### Post by bilol on 2010-01-07
Any solution?????
Or I have to format the disk????

---

### Post by bilol on 2010-01-12
I managed to take the back-up and have to format the disk in vfat.
Now it is working well......

---

### Post by MyR on 2010-01-13
One limitation to FAT filesystems is that files cannot be larger than 4GB.

---

