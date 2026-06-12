---
title: "vaio vgn-sr19vrn only 2.9 gb memory detected"
date: 2009-05-18
forum: Hardware
---

### Post by exhauster on 2009-05-18
Hi.
I have installed on my laptop ubuntu 8.10 and 9.04 but both systems have the same problem, they are detecting only 2.9gb of memory instead of 3.2 or 4.
free -m 
                   total       used       free     shared    buffers     cached
Mem:          2992       1182       1810          0         47        337
-/+ buffers/cache:        796       2196
Swap:         3906          0       3906

uname  -a
Linux victim 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686 GNU/Linux

Does anybody have any ideas?
Thanks in advance!

---

### Post by Barry Carroll on 2009-05-19
I would wager that you are seeing this because you are running 32-bit Ubuntu and some of your memory is being stolen by your graphics card.

---

