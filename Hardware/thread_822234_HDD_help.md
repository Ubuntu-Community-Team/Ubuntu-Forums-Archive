---
title: "HDD help"
date: 2008-06-08
forum: Hardware
---

### Post by reyn8414 on 2008-06-08
And no one can help me. Including Vista.
Im refurbishing my laptop for donation. and i need to put vista back on there.
my computer is an acer Extense 4620z, And i completely installed ubuntu on my hard drive for quite some time. Well i just reformatted to NTFS not properly removing ubuntu. And Acers partition software wont detect my harddrive. 
The vista recovery disk wont install vista. because it says its missing ( Whats missing is D:\Sources\Install.Wim ) So basically, i know this is more vista related. but no one else can help me.

I can post more info as required :]
Thanks in advance,
Ryan

---

### Post by alguin2 on 2008-06-08
Why don't you re-install the latest Ubuntu, with all the Open Source Office Apps, etc that a user can use? Also, setup the desktop and menus for user-friendlyness, and writeup a small manual?  You can hide the package manager and update manager to prevent the would-be user from shooting him/herself in the foot with a buggy update.

---

### Post by woodcarver on 2008-06-08
I would leave Umbuntu on it too. 
Vista won't install because there were still parts of Umbuntu on the HDD. You would have to delete and create partitions several times to clear it off.

---

### Post by grth on 2008-06-08
Hi

Can understand others saying leave Ubuntu on it, but if you want Vista then you want Vista.

You don't say if your Acer is setup with a recovery partition on the HD and if that is what the recovery disk is trying to find and it has been wiped.

If that is the case then, you may not be able to get round this.  If that is not the case and the recovery disk will completely redo the HD, then the option might be to wipe the HD and re-try.  GParted is a good tool for managing the HD and will certainly wipe the HD.

However, it does not sound as if the Recovery Disk will operate by itself?

The other thing that might need to be done is to re-install the MBR for Vista.  Vista only likes it's own bootloader, so fixing that might be part of the issue.

If you only have a recovery disk that works with a recovery partition, then the other thing to do is contact Acer for a full copy of Vista.  They are obliged to do this and it won't cost the earth.  Have heard of figures around £10 - £25.

Finally, the other place to get some help is from [www.neosmart.net/forums/](www.neosmart.net/forums/)

This site has helped me no end as I have been attempting to build a triple boot system.  They seem to know a lot about Vista.

---

