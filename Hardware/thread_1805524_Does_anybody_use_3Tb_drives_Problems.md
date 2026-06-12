---
title: "Does anybody use 3Tb drives? Problems?"
date: 2011-07-16
forum: Hardware
---

### Post by Moozillaaa on 2011-07-16
I have 9.5Tb drive space in my computer, and it's full of movies (2 x 2Tb, 4 x 1.5Tb), and I want to get them transferred to some 3Tb drives.

Is there software in the repos that recognizes these drives?


edit:
Looks like in Windows environments, up to 280G is not usable on these drives????????

---

### Post by cchhrriiss121212 on 2011-07-16
It depends on the partition table you use, the ms-dos table has a limit of 2TB. So you would just need to format the drive then use a gpt partition table, which you can do with gparted.

---

