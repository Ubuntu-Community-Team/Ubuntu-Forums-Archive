---
title: "disk space dillemma"
date: 2009-10-27
forum: Hardware
---

### Post by jeff00z28 on 2009-10-27
I built a backuppc server several months ago. When I set it up it wouldn't let me use the full 4tb raid, it would split it up as shown in this gparted window i snapped a screenshot of. Now The 2.00tb partition that has the backups on it is completely full so I can't backup anymore. I really need the rest of that space. It was running smoothly until we had to add a 700gb partition and that kinda screwed it all up. If anyone has any idea how I can make use of that other partition, or merge them somehow help is needed. Also this is not the root file system, it resides on a separate raid 1. Thanks.

[IMG]http://i39.photobucket.com/albums/e194/jeff00z28/ubuntudisk.jpg[/IMG]

---

### Post by jeff00z28 on 2009-10-28
ttt

---

### Post by quimkaos on 2009-10-28
o damn i nead one just like that

just a question... why ext2?

---

### Post by jeff00z28 on 2009-10-28
> **quimkaos said:**
> o damn i nead one just like that

just a question... why ext2?

i tried ext3 and 4 a well and the same issue occurred

---

### Post by parameter on 2009-10-28
Will gparted let you resize the partition if you run it from a live CD? ext2 should be able to go larger than 2TB as long as you are using at least kernel 2.6.x.

---

### Post by jeff00z28 on 2009-10-29
hmm i will try the live cd. Right now it is just grayed out. Its not even the root partition which is weird.

---

