---
title: "Wubi On External Hardrive"
date: 2008-10-10
forum: General Help
---

### Post by Thecoolguru on 2008-10-10
Hey,
I kinda ran out of hard drive space, and I want to install Wubi on an external hard drive. Is this possible? There is probably some file that tells the program where to look for the kernel, so if I edit that path, won't it work? I'm not entirely sure what to do. Help would be greatly appreciated. Thanks in advance!

---

### Post by mikedep333 on 2008-10-12
Are you saying you want to move it over from an internal to an external hard drive, or reinstall it?

---

### Post by igorel on 2008-10-12
> **mikedep333 said:**
> Are you saying you want to move it over from an internal to an external hard drive, or reinstall it?

he wonders if he can do any of doese things... and how?

---

### Post by ago on 2008-10-13
You can install over an external drive or move an existing installation over an external drive by simply moving the ubuntu folder.

In the second case make sure you edit ubuntu/disks/boot/grub/menu.lst and change all the root=UUID=... lines in there. You can replace with /dev/sdXX where XX is the drive and partition (e.g. root=/dev/sdb4 for partition 4 of drive 2) or you have to find out the UUID of the new host partition.

---

