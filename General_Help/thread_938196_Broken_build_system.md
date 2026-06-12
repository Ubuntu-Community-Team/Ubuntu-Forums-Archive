---
title: "Broken build system"
date: 2008-10-04
forum: General Help
---

### Post by squaregoldfish on 2008-10-04
Up until a week or so ago, I've been merrily compiling stuff using gcc (Fortran, C, C++...) without a problem. Then it stopped working - every time I try to build something, I get the following error.

```
collect2: cannot find 'ld'
```

ld exists in the location that the build system expects (/usr/bin/ld), and I can call it from the command line without any problems.

I've reinstalled the binutils package, together with all the gcc packages that I have installed, but to no avail.

I've got no idea what's gone wrong. Can anyone give me any clues?

Thanks,
Steve.

---

### Post by squaregoldfish on 2008-10-17
Update:

I've discovered (through suggestions elsewhere) that if I ssh into my box I can compile stuff just fine. If I try to compile locally, I get the errors above. This implies there's something wrong in the environment settings somewhere.

I'll have a look at this over the weekend, but in the meantime if anyone has any suggestions I'd be grateful.

Steve.

---

