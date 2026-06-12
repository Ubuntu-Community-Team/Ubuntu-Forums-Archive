---
title: "Frustrated with external USB drive"
date: 2008-11-29
forum: General Help
---

### Post by GuiGuy on 2008-11-29
I have a Maxtor 500G external USB (NTFS) drive that I have been using for some time on Windows and Ubuntu boxes, without hassle. I take care to unmount the device before disconnecting it. 

Today, for no reason, on the three Linux PCs I have tried, the device comes up as being a "read only file system".

no amount unmounting, changing owners, permissions etc changes that. Every action gives a "mounted as read only" error. 

I have no idea what to do next. Any help?

NB: The drive works fine on WinXP

---

### Post by soro2005 on 2008-11-30
You could check in Windows whether the file system is intact. With ckdsk /f

---

### Post by GuiGuy on 2008-11-30
> **soro2005 said:**
> You could check in Windows whether the file system is intact. With ckdsk /f

Thanks. I'd done that already. The disk is good. I'd repartition & re-format the thing in ext2 or ext3 if I didn't need it to work on Windows boxes :(

Cheers

---

