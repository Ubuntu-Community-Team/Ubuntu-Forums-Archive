---
title: "Help with mounting a (damaged?) partition"
date: 2011-06-30
forum: Hardware
---

### Post by Vostrocity on 2011-06-30
I have an NTFS partition that I use solely for personal files I need to access in both Ubuntu and Windows.

Last week, I got a trojan in Windows that wiped out my Master Boot Record so I couldn't even get to GRUB, much less boot up to any OS. I used a Ubuntu LiveCD to restore GRUB, and now both OS's boot up fine. The problem is, I can't access that extra NTFS partition in either Windows or Ubuntu. They both see the partition, but won't let me open them. When I try to mount it in GParted, it says "you must specify file system type". But in the File System column, it already displays NTFS. 

Thanks in advance.

---

### Post by TechSupportx86 on 2011-06-30
go into windows and run:

```
chkdsk /f X:
``` (X being the drive letter)

and let it check the filesystem. If it's just damaged it should fix it. There is probably a way to do it in ubuntu, but since it's NTFS i would do it under windows.

---

