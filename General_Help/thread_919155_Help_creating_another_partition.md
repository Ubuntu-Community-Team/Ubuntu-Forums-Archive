---
title: "Help creating another partition"
date: 2008-09-13
forum: General Help
---

### Post by pampilhoso on 2008-09-13
Right now i have 4 primary partitions (/, home, swap, windows) and 8gb unallocated disk space. I want to create a 5th partition, but ubuntu won't let me, because i hit the limit of 4 primary partitions. I read that an easy way to create another partition is to remove one and then create logic/extended partitions, the problem is, the only partition that i can remove to the trick is the swap partition. Can anyone predict the problems that will arise and possible solutions, after i recreate the swap artition using ubuntu live cd?

---

### Post by RealPSL on 2008-09-15
Unless you are hibernating the swap partition does not hold any persistent data. As long as you put a swap partition back in place you should not encounter any problems.Just remember to back your data on the other partitions before making the changes as we are all human and make mistakes.

---

