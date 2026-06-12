---
title: "partition issue!"
date: 2008-10-14
forum: General Help
---

### Post by Mowk on 2008-10-14
Hey guys, I booted up in ubuntu and i clicked install, to see what it was then i didnt really want to partition my drives. so i used 20 gigabites of my hardrive but i diddnt evenm install it jsut resized them, is there a way to put them back to normal so im not missing 20gb?!
thanks

---

### Post by drs305 on 2008-10-14
> **Mowk said:**
> Hey guys, I booted up in ubuntu and i clicked install, to see what it was then i didnt really want to partition my drives. so i used 20 gigabites of my hardrive but i diddnt evenm install it jsut resized them, is there a way to put them back to normal so im not missing 20gb?!
thanks

Did you lose data that you are trying to restore? If you just need to resize it back to normal without trying to recover lost data, there is an app on the livecd called 'gparted' which can resize partitions. 

You access it from the livecd desktop: System, Administration, Partition Editor. As with any kind of disk operations, try to backup any data you might be putting at risk if possible.

If you are trying to restore data that you may have lost, there are apps like 'testdisk' that are good at recovering from partition mistakes. Search this forum for more information on testdisk.

Here's a link for testdisk:
[http://http://en.wikipedia.org/wiki/TestDisk]("http://http://en.wikipedia.org/wiki/TestDisk")

---

### Post by Yellow Pasque on 2008-10-14
Boot the LiveCD and go to System -> Administration -> Partition Editor
Make sure you know what you're doing.

---

### Post by jerome1232 on 2008-10-14
Yes if you open gparted from the live cd. (System->Administration->Partition Editor) you should be able to grow the file system back up to it's original size.

**I always recomend getting your backups up-to-date before editing partitions.**

---

### Post by tuxxy on 2008-10-14
Heres a guide for when you install it properly

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

