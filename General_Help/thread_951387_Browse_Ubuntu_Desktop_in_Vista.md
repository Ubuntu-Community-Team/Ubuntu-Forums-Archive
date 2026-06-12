---
title: "Browse Ubuntu Desktop in Vista?"
date: 2008-10-18
forum: General Help
---

### Post by iampriteshdesai on 2008-10-18
i have installed Ubuntu on Vista using Wubi. Now I can use Vista's folders like Desktop, Music, Documents in Ubuntu but I cannot find the files kept in Ubuntu's Pictures, Video folder when I boot into Vista. How can I browse Ubuntu Desktop and other folders while in Vista?

---

### Post by TenPlus1 on 2008-10-18
As far as I'm aware wubu.exe installs Ubuntu in a virtual partition file which is mounted during boot (if selected), so Vista cannot see inside this virtual file ...but... if Ubuntu was installed as a proper dual-boot configuration (it's own partitions) then you could install Ext2Fs and that will let Vista view Ext2/3 partitions...

[http://e2fsprogs.sourceforge.net/ext2.html](http://e2fsprogs.sourceforge.net/ext2.html)

---

