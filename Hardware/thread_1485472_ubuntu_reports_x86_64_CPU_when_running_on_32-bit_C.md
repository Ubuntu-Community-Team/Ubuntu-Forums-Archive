---
title: "ubuntu reports x86_64 CPU when running on 32-bit CPU"
date: 2010-05-16
forum: Hardware
---

### Post by cliffordis on 2010-05-16
I hope this is the right section for this.  I'm running ubuntu 10.04 (though I had the same problem with previous versions) with wubi.  I couldn't find anything else on this, so I apologize if it's already been discussed.  Problem is that my CPU is 32-bit (Pentium 4), but ubuntu reports "x86_64" when I run 'uname -m'.  Otherwise the system runs fine and I wouldn't bother, but I'm trying to install a .deb and it gives me the "wrong architecture" error.  Obviously I also get an error if I try to install the 64-bit version of the package.

Any help?  Have I missed something huge?

-Clifford

---

### Post by bhaverkamp on 2010-05-16
uname -a
cat /proc/cpuinfo - look for flags 'lm'

There are 64 bit versions of the Pentium 4, Intel introduced the instructions with the Pentium 4 G1 step in December 2005.

---

### Post by cliffordis on 2010-05-16
uname -a outputs the following:
```
Linux ubuntu 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:28:05 UTC 2010 x86_64 GNU/Linux
```

---

### Post by cliffordis on 2010-05-16
Nevermind, it's a 64-bit Pentium 4.  I could have sworn it was 32-bit.

---

### Post by cascade9 on 2010-05-17
> **bhaverkamp said:**
> There are 64 bit versions of the Pentium 4, Intel introduced the instructions with the Pentium 4 G1 step in December 2005.

As far as I know, there were 64bit P4s around well before December 2005. (june 2005 at the latest...no idea if that was just a typical intel 'paper launch' though). 

There are also E0 stepping P4s that are 64bit compatible

---

