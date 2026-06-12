---
title: "Different Formats for Different Partitions"
date: 2008-10-14
forum: General Help
---

### Post by carterw65 on 2008-10-14
Hey All!

I have a 500GB ext hdd that I use solely for backing up my computers. I am wondering if I partition it can I format a partition to use with Ubuntu to back up my Ubuntu machine. This would get me one step closer to eliminating Windows for good!

Thanks!

---

### Post by linux_lover69 on 2008-10-14
Of course

---

### Post by Sam on 2008-10-14
You can use ext3 (or any other linux filesystem) for any kind of drive.

Later if you need to access your ext3 partition within Windows, use [Ext2 IFS for Windows](http://www.fs-driver.org/).

---

### Post by carterw65 on 2008-10-14
Care to through me a bone here? Never done this kind of thing before. I would have to do it from Windows as it currently has data I do not want lost and is NTFS.

---

### Post by linux_lover69 on 2008-10-14
You can backup in NTFS. I think its easier that wAy

---

### Post by Sam on 2008-10-14
Yep backup everything in Windows, then boot to Ubuntu and use "System / Administration / Partition Editor" to format your drive (be careful to choose the right one ;)). Ask if you need more help.

---

### Post by carterw65 on 2008-10-14
I will have to figure out how to backup my backup :) Thanks a bunch!

---

