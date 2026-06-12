---
title: "wont install on HP Pavilion dv2601tu notebook"
date: 2010-07-17
forum: Hardware
---

### Post by imkaushal on 2010-07-17
The only reason I know is because the notebook has dynamic hard drive(probably due to pre-installed Windows Vista).
I have upgraded now to Windows 7 Ultimate.
I can neither install ubuntu(10.04 / 9.10) inside windows nor by deleting a volume(keeping it as unallocated space)
Ubuntu does not detect the unallocated space...
Thanks in advance....

---

### Post by imkaushal on 2010-07-18
Please help me anyone....
Thnaks...

---

### Post by PresenceofMind on 2010-07-18
Hello,

May I suggest Wubi? If you can create a partition using Windows Disk Management software, I'm sure Wubi can get Ubuntu to install in that partition. All you have to do is access the LiveCD and double click Wubi.

Hope this helps.

---

### Post by theozzlives on 2010-07-18
> **imkaushal said:**
> The only reason I know is because the notebook has dynamic hard drive(probably due to pre-installed Windows Vista).
I have upgraded now to Windows 7 Ultimate.
I can neither install ubuntu(10.04 / 9.10) inside windows nor by deleting a volume(keeping it as unallocated space)
Ubuntu does not detect the unallocated space...
Thanks in advance....

Have you tried partitioning manually? When you get to the partitioner, there's an option to do it manually. You'll want ext4, and a mount point of "/". Vista or 7, Ubuntu should install.

---

### Post by imkaushal on 2010-07-23
> **PresenceofMind said:**
> Hello,

May I suggest Wubi? If you can create a partition using Windows Disk Management software, I'm sure Wubi can get Ubuntu to install in that partition. All you have to do is access the LiveCD and double click Wubi.

Hope this helps.
Wubi was my 1st try..it saw the partition created by win disk management but at the end of installation...it gave error about bcdedit.exe

[QUOTE=theozzlives]Have you tried partitioning manually? When you get to the partitioner, there's an option to do it manually. You'll want ext4, and a mount point of "/". Vista or 7, Ubuntu should install.[/QUOTE]

I have the following partitions:
1. Windows 7(C: )     - 27GB
2. HP_Recovery(Z: )   -  8GB
3. For data/media(A: )- 48GB
4. For data/media(D: )- 63GB
(All are NTFS)
Ubuntu partitioner shows A: , D: and Z: as one single drive combined!
If I try to change it all my data will be lost...
I tried backing up data from A: and deleted it.
Even then ubuntu partitioner doesn't detect free space...

Is there another solution?

Thank you guys....

---

