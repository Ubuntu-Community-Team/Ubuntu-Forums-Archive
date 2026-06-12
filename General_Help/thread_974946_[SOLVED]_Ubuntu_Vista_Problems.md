---
title: "[SOLVED] Ubuntu Vista Problems"
date: 2008-11-08
forum: General Help
---

### Post by Brian R. on 2008-11-08
Have a desktop with Ubuntu 8.04 and a laptop running XP, both couls see each other and read and write to their shared folders. But now have a laptop running Vista. Vista can see and read and write to Ubuntu shared folders, but Ubuntu can only see the shared folders on the Vista machine, it cannot see the files, says it cannot mount the drive??. Changed the workgroup in Samba from MSHOME to WORKGROUP to match Vista but no luck.
Is the problem with Samba or Vista?

Brian R.

---

### Post by madverb on 2008-11-08
Vista

---

### Post by Brian R. on 2008-11-10
Thank you Madverb, that narrowed my search for a solution down, it was Vista's clumsy security system causing the problem. Had to activate the guest account.

---

### Post by madverb on 2008-11-15
Haha, no worries

---

