---
title: "why can't I find my disk?"
date: 2008-09-01
forum: Hardware
---

### Post by Layor on 2008-09-01
Hi all, 
I have three HD's, one C:40Gb (XP) one E:15GB (data) and one F:40Gb with Ubuntu. Why, when I go into XP, can I not see my F: Ubuntu disk?
I have some problems and was going to re-format the drive and start again. Can anyone help. please?

---

### Post by ubutufan on 2008-09-01
Hi Layor

You cannot "see" the disk with ubuntu from xp.
That is because xp will recognize only ntfs or fat file systems.
Ubuntu installation is done on ext3 file system which is not recognized by xp.
However ubuntu can read & write on ntfs file systems

If you want to share files between xp and ubuntu, then they should be saved on ntfs or fat file systems.

I hope that clears the scenery for you.

---

