---
title: "I get an error during install"
date: 2009-05-07
forum: Installation &amp; Upgrades
---

### Post by Fandorin72 on 2009-05-07
I run windows xp sp3, and wanted to dual boot it with Ubuntu 9.04. But during the initial stages of that installation, i always get this error:
[[IMG]http://pic.ipicture.ru/uploads/090508/thumbs/9GHCT4WTS0.jpg[/IMG]]("http://ipicture.ru/Gallery/Viewfull/18593727.html")
 
I havent yet partitioned my HD, but on the other hand, when i inserted the Ubuntu CD, it told me that it is possible to perform an installation within windows obviously without the need of partitioning the HD first...so, what ya think i am doing wrong?:o

---

### Post by jpseixas on 2009-05-07
Why don't you try to run the install disk directly from boot, instead of runnig it under windows?

The installation CD is bootable, and you will still have the option of a dual boot.

Remember to defrag the windows disk first, so you can create the Linux partition on a continuous free disk space.

---

### Post by Fandorin72 on 2009-05-07
Thanks 4 the promt reply :) so u re sayin i should first partition the HD to allocate the space for Linux, correct? I heard that 30 GIG is even more than necessary...but i also was told that i have to create separate partition for Linux's swap file and place it b4 the actual Linux partition...i m really confused allready:(
I am using Partition Magic

---

### Post by jpseixas on 2009-05-08
No, I'm saying to run the install directly from boot, instead running it in windows.

You don't need to create the partitions before running the install. Let Ubuntu do it for you. It will preserve the windows partition, and let you choose the size for using with Ubuntu. I only said to **defrag** the disk before running install...

---

### Post by HyRax on 2009-05-08
> **Fandorin72 said:**
> I havent yet partitioned my HD, but on the other hand, when i inserted the Ubuntu CD, it told me that it is possible to perform an installation within windows obviously without the need of partitioning the HD first...so, what ya think i am doing wrong?:o

Ubuntu can be install two different ways - the FIRST is the one you are looking at right now - installing Ubuntu as though it were just another Windows application. You don't need to repartition your drive and is installs as one big huge file on your Windows partition. You still restart your computer to launch it, but it can be uninstalled by going to Windows' Add/Remove Programs. The problem with installing via this method is that drive access is a little slower than it should be.

The SECOND way Ubuntu can be installed is the more traditional way, by starting up your PC on the CD (not Windows first). This process will shrink the Windows partition to a smaller size to allow a second partition to be created on your hard-drive to install Ubuntu on. This is a direct native installation and will make Ubuntu perform at its best.

Now I can't address that specific error you're having as I've never seen it, but you are better off doing a native install of Ubuntu in a separate partition, or if you don't want to do that, consider setting up a Virtual Machine within windows to play with Ubuntu using Virtualbox or similar virtualisation app.

---

### Post by Fandorin72 on 2009-05-12
Thanks so much :) I found out, that i dont really like it (not as much as XP anyways), but its kinda neat OS:popcorn:

---

