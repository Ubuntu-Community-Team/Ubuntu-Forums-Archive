---
title: "what is equivalent to defragment in Linux??"
date: 2008-10-05
forum: General Help
---

### Post by ra2008 on 2008-10-05
Hi,

In windows there is defragment tool for the disk drives. what is equivalent in Linux?? or any tool to check and repair HDD??
thanks

---

### Post by LoneWolfJack on 2008-10-05
due to the different concept of the file system, linux doesn't need a defrag tool.

---

### Post by cariboo on 2008-10-05
THere are some defragmenting utilities floating around, but they are not needed. Linux doesn.t use a shotgun style to write data to a disk like windows does. Have a look at this:

[http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting](http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting)

It will explain why Linux doesn't need defragmenting.

Remember linux is not windows, most of what you know about computers doesn't apply here.

Jim

---

### Post by eldragon on 2008-10-05
> **cariboo907 said:**
> 
Remember linux is not windows, most of what you know about computers doesn't apply here.

Jim

and most stuff you didnt know about computers DO apply here :D

---

### Post by ra2008 on 2008-10-06
> **eldragon said:**
> and most stuff you didnt know about computers DO apply here :D

thats why i like linux;)

---

### Post by jerome1232 on 2008-10-06
Technically ntfs is fragmentation resistant too, it just has this page file (linux uses a dedicated swap partition instead of a page file) stuck in the middle of the drive that is constantly changing in size, hence more fragmentation.

ext3 CAN fragment when the disk gets near full. It tries to avoid fragmenting files whenever possible. The best defrag tool is to simply move everything to a different drive then copy it back. I believe fsck (the equivalent of chckdsk for windows) can report on file fragmentation.

---

### Post by c4tly5t on 2008-10-06
> **LoneWolfJack said:**
> due to the different concept of the file system, linux doesn't need a defrag tool.

wooo linux :lolflag:
but yeah you dont need to defrag and you dont need annoying anti virus

---

