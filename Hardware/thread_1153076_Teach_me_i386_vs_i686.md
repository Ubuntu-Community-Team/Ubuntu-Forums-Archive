---
title: "Teach me: i386 vs i686"
date: 2009-05-08
forum: Hardware
---

### Post by Kareeser on 2009-05-08
Hey guys,

Even after reading the Wikipedia articles on both i386 and i686, I still don't quite grasp the definition behind i386 and i686.

Ubuntu releases i386 and x86_64, nicknamed "32-bit" and "64-bit".
Arch releases i686 and x86_64, also nicknamed "32-bit" and "64-bit", I think?

So what exactly is the difference? After reading some posts on UF and on the web, it **seems** to be that i386 is just the "lowest common denominator", in that with Ubuntu compiled for that architecture, you get to support almost ALL systems, down to the oldest Pentiums, whereas i686 begins at a certain technological level, and won't support legacy systems, but runs faster, since it's optimized for faster architectures.

Am I correct, or am I completely missing the point?

---

### Post by hardyn on 2009-05-08
in your specific example, its probaby just naming.

in a more generic sence, you are right i386 is the lowest common denominator, 32bit with standard x86 instuction set.  i686 will imply inclusion of some of the later hardware optimizations, like mmx, sse1/2/3, and others.

as these optimisations are avalable in the i386 packages for ubuntu, it has just become a naming convention.

---

