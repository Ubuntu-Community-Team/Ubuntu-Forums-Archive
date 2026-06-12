---
title: "Cannot Browse the disk where i installed wubi(ubuntu)"
date: 2008-08-22
forum: General Help
---

### Post by C.U.B.E.M.A.N on 2008-08-22
Wubi works just fine, but i cant seem to find the C: drive in my computer. i find my D: drive, but the drive that says "File System" has only the ubuntu install,(not very strange), and i would like to find my C: drive.


Thanks.

---

### Post by timcredible on 2008-08-22
are you wanting to view your windows partition on the drive?  if so, you need to mount it before browsing it.  in the file browser, find the drive on the left pane that is your windows partition, right-click and choose 'mount', then you can browse it.

---

### Post by C.U.B.E.M.A.N on 2008-08-22
> **timcredible said:**
> are you wanting to view your windows partition on the drive?  if so, you need to mount it before browsing it.  in the file browser, find the drive on the left pane that is your windows partition, right-click and choose 'mount', then you can browse it.

Yes, that would be possible IF the drive was there. but its not.
Screene:[IMG]http://img367.imageshack.us/img367/4407/screenshotcomputerfilebtx3.png[/IMG]

---

### Post by rokytnji on 2008-08-22
File system is where Windows is.

---

### Post by C.U.B.E.M.A.N on 2008-08-22
NO, on wubi, ubuntu is installed on a .drive file, in C:
[IMG]http://img353.imageshack.us/img353/4388/screenshotdevsdagpartedur3.png[/IMG]
sda1 is "filesystem" or ubuntu
sda2 is C: drive and is the one that i cant find(it has Vista on it)
sda3 is D: and works fine

---

### Post by Paaske on 2008-12-17
Your Window files are located under /host

-- 
/Christian

---

### Post by C.U.B.E.M.A.N on 2008-12-17
Yeah, i found out a while ago, but thanks :-)

---

