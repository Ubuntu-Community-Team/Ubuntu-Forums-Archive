---
title: "Data loss on external harddrive? Input/Output errors"
date: 2015-11-07
forum: Hardware
---

### Post by simon121 on 2015-11-07
My external harddisk used to work well, but suddenly

-Dolphin file manager shows that almost all music and movie files have disappeard
-Those files that can still be seen don't work when I open them (in VLC, I get an input/output error)
-Also when opening other file types (pdf, etc) I get an input output error.
-using the 'ls' command, ls says "ls: cannot access ***: input output error"

However, the df command still shows tha the ext drive is almost full

What happened to my drive, and how can I fix this?

My external hard drive is formatted with ext4 and encrypted.

Thanks.

---

### Post by sudodus on 2015-11-07
It might be a damage of the file system, a software problem, or a damage of the hardware, where the data is stored, bad sectors or bad blocks.

If you suspect a hardware problem, and the data are valuable, you should start by cloning the drive to another drive of at least the same size. You can use ddrescue for that task.

```
sudo apt-get install gddrescue
```
```
man ddrescue
```

-o-

If you do not suspect a hardware problem, you can try to repair the file system with one of the following commands.

If it is a Windows file system, FAT32 or NTFS, boot into Windows and run

```
chkdsk /f X:
```

where X: is the Windows volume letter of the external harddisk.

If it is a linux ext2, ext3 or ext4 file system, boot into linux, unmount the partition(s) on the external harddisk and run

```
sudo e2fsck -f /dev/sdxy
```

where x is the linux drive letter and y is the partition number, for example /dev/sdb1.

-o-

Have you rebooted your computer?

Have you tried in another computer, or with another port and another cable?

---

