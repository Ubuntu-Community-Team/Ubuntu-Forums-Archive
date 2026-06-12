---
title: "i686 kernel?"
date: 2007-04-30
forum: Hardware &amp; Laptops
---

### Post by Circleback on 2007-04-30
Is there an i686 kernel in the Ubuntu repos like in the Debian repos?  Or do I gotta compile a custom one. If so can anyone point me in the right direction to compile a i686 kernel.

Thanks

---

### Post by phin on 2007-04-30
just run the generic kernel.  it will automagicly put in options for whatever processor it detects.

---

### Post by hardyn on 2007-04-30
the i386 kernel would be suitable too (esp. if you have a sony P-M notebook)
the i386 is now a 686 kernel w/o SMP.

---

### Post by az on 2007-04-30
The generic kernel replaced the 386 kernel.  The 686 compile-time optinons are not just compile-time anymore.  The 686 optimisations are loaded at run time.

No, you don't need to compile/install the 686 kernel.

---

### Post by A. J. Rimmer on 2007-05-01
Here is a link to a discussion on the subject.  I am running Dapper and followed the instructions here to upgrade from the 386 to the 686 kernel.  This was a few months back; don't know if this is still relevant or not.

[http://ubuntuforums.org/showthread.php?t=85917&highlight=kernel+dual+core+i686](http://ubuntuforums.org/showthread.php?t=85917&highlight=kernel+dual+core+i686)

---

