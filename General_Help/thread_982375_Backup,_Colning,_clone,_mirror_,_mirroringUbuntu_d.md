---
title: "Backup, Colning, clone, mirror , mirroringUbuntu drive"
date: 2008-11-14
forum: General Help
---

### Post by lcs81 on 2008-11-14
Hi all,

Assume i have a PC with a single drive with Ubuntu installed. I would like to create a "backup" onto another drive physically. 

I put quote on the word backup because i am not sure if this a proper term to be used.

My objective of doing this, is when my primary drive (drive 1) crash physically, i can quickly swap with the backuped/clone drive (drive2).  

Doing this i would assume not major re installation required as i can only allow the system to be off for minimal of time. 

Is there any way of doing this? I try to find some forum and internet, i found 2 way to doing "clone". 

First is using dd => dd if=/dev/sda of=/dev/sdb. Well, i found that the "clone/backup" does not really "clone" exactly. I figuring out by exploring the files. Using ls -la also found that the "cloned/backuped" has loss all the "permission"
(From [http://lists.samba.org/archive/rsync/2002-August/003409.html](http://lists.samba.org/archive/rsync/2002-August/003409.html))

2nd, is use command CP -a. By the way, i am looking for the solution where drive1 is a system drive and drive 2 is a backuped drive. I should able to clone/backup from time to time. Once if drive1 failed physically, i can immediate replace from the drive2.   (From: [http://ubuntuforums.org/showthread.php?t=470623](http://ubuntuforums.org/showthread.php?t=470623))

Thanks for the help

---

### Post by Steve1961 on 2008-11-14
clonezilla sounds like what you're looking for:

[http://clonezilla.org/](http://clonezilla.org/)

Download the live cd and use that

---

### Post by lcs81 on 2008-11-14
Thanks Steve1961. 

By the way, i am new to Linux and i would like to learn more. There is no way for us to write our own script of doing "cloning"?

---

### Post by Steve1961 on 2008-11-14
Well I'm sure there is a way to write a script to do this automatically because there;s many ways to clone a drive when using Linux.  See, for example, this article:

[http://www.linux.com/feature/152592](http://www.linux.com/feature/152592)

However, I'm no expert at writing scripts so I tend to stick to what's easy, and have found clonezilla does the job.

Maybe someone else has some suggestions for a disk cloning script?

---

