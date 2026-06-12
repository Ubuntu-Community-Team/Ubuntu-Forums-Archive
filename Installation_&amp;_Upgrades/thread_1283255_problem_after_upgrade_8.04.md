---
title: "problem after upgrade 8.04"
date: 2009-10-05
forum: Installation &amp; Upgrades
---

### Post by n.d.turnip on 2009-10-05
I have a problem after upgrading from ...-23-386 to ...24-386. On booting I get 'Error 18: selected cylinder exceeds maximum supported by BIOS', the machine (IBM Thinkpad X31) is working fine with the earlier kernel.
Any advice please.

Ta

---

### Post by n.d.turnip on 2009-10-06
Still got 'Error 18' problem, any advice please

I am not dual booting into Windows and I have tried:

nick@nick-laptop:~$ sudo fsck /dev/sda1

fsck 1.40.8 (13-Mar-2008)
e2fsck 1.40.8 (13-Mar-2008)
/dev/sda1 is mounted.  



/dev/sda1: recovering journal
Clearing orphaned inode 1983659 (uid=0, gid=0, mode=0100600, size=80)
Clearing orphaned inode 983340 (uid=1000, gid=1000, mode=0100600, size=0)
Clearing orphaned inode 1982931 (uid=1000, gid=1000, mode=0140755, size=0)
/dev/sda1: clean, 165639/4685824 files, 8452323/9361870 blocks
nick@nick-laptop:~$ sudo e2fsck -C0 -p -f -v /dev/sda1
/dev/sda1 is mounted.

---

### Post by Bucky Ball on 2009-10-06
This might help:

[http://members.iinet.net.au/~herman546/p15.html#18](http://members.iinet.net.au/~herman546/p15.html#18)

---

### Post by n.d.turnip on 2009-10-07
Thanks, this is a really helpful page for anyone who gets an Error 18 message. Not least for a relatively untrained user of Linux like me to understand what the problem is.

[http://members.iinet.net.au/~herman546/p15.html#18](http://members.iinet.net.au/~herman546/p15.html#18)[/QUOTE]

I solved the problem by re-installing the kernel.

---

### Post by Bucky Ball on 2009-10-07
Excellent! Please mark the thread as solved to help others from 'Thread Tools' at top of this page. :)

8.04 Rocks!

---

