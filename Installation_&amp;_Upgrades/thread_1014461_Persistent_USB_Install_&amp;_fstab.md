---
title: "Persistent USB Install &amp; fstab"
date: 2008-12-17
forum: Installation &amp; Upgrades
---

### Post by chiefchief on 2008-12-17
I just created my media computer for downstairs using some fairly decent hardware (p4 & ati pci-e card) and installed ubuntu 8.10 to a 4gb flash drive (I had no other hard drives).

The plan is to have the OS run on the tiny mem stick with a little bit of space for new programs, and have the fstab automount the samba shares from my NAS that has all my music and movies.

Everything works great (compiz looks sooooo awesome), but the fstab will clear itself on reboot.  Seems like I have a persistent flash drive with the exception of the fstab.

I've searched around on the forums (as any good poster does) and I have not found a similar issue to this.  Is there anyone out there that can help me?  Much appreciated!

(also, I think ubuntu is the proper prefix for this thread.  Or would it be Gobuntu?)

---

### Post by chiefchief on 2008-12-18
*bump*  Someone has to know this question.

---

### Post by pietjanjaap on 2008-12-18
Maybe you need a service/program that runs in the background, but wen you start de pc it is not running.
But wen you connect manual then that program gets started.

Or

Maybe you need to put something in the fstab, like always connect.
gksudo pysdm, install this, start it.
Look if you can save it in a different way, this is with gui. The  nas server.

---

