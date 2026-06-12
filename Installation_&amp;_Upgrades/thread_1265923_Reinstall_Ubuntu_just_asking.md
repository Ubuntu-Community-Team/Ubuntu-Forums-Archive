---
title: "Reinstall Ubuntu just asking ?"
date: 2009-09-14
forum: Installation &amp; Upgrades
---

### Post by NawafLol on 2009-09-14
i'm using ( Duel boot ) i had a nasty bug with my ubuntu and i want to reinstall it !

so just asking how ? and if it will effect my windows 

i have my ubuntu cd so can anyone help me !

---

### Post by Partyboi2 on 2009-09-14
When you reinstall choose the "Manual" Partitioning option when you get to the partitioning stage and  choose to edit your Ubuntu ext partition, then reset the mount point to / and choose the file system for that partition usually ext3. Then tick the box to format that partition. 
If you have a separate /home partition reset the mount point for it to /home But*** do not*** tick the box to format it.
Then continue with the install, reinstalling Ubuntu should not effect your windows install.

---

### Post by NawafLol on 2009-09-14
can i reinstall but without no data lost !

---

### Post by Partyboi2 on 2009-09-15
If you do not have a separate /home partition you can create one following [[COLOR=Blue]this[/COLOR]]("http://www.psychocats.net/ubuntu/separatehome"). The advantage of having a separate /home partition is that all the data like your documents, videos, music, user settings etc... are untouched if you ever need to reinstall.

---

