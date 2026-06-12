---
title: "Acronis software in all LInux"
date: 2008-08-13
forum: General Help
---

### Post by willieboy on 2008-08-13
I have not seen anything on this software in any Linux forums.

Acronis True Image 11
Acrtonis Disk Director 10.

They both work with Linix- but not in Linux.
You need both programs to run in window then you make a recovery CD  from either one, I used True Image, no reason why I did.
Not only does it install TI in the cd, but also Disk Director.

To use the CD, on startup the PC insert the cd in the CD/DVD rom and let it run. 
You will have the option of using either of the programs.

DiskDirector will allow you to setup Linux partitions ands drives, I prefer this program than gparted, much better to work with.
Then TI will make disk images of your Linus partitions to another drive or partition, then it will restore them as and when you want to do so.

e.g., you do something in Ubuntu, it goes wrong, more than likely you will need to re-install, but not with TI.  Just restore the image you made.

I just thought I'd pass this on as someone may be interested.

---

### Post by kpkeerthi on 2008-08-13
You can create/restore disk images with **partimage/clonezilla**
For differential/incremental backup use **rsync/rsnapshot**
There is also **tar**

---

