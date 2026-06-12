---
title: "Can't compile manufacturer driver"
date: 2024-11-06
forum: Hardware
---

### Post by peyre on 2024-11-06
I installed a PCI-e card and it works on my system, but it came with a linux driver and I thought that might let me change settings on the card for better performance.

The README for it says:

> 1. open "Terminal"

2. cd "driver" directory

3. compile the driver using "make", you will see the module "wch.ko" if successful

4. "insmod wch.ko" to load the driver dynamically

5. "make install" to make the driver work permanently

The files in the driver directory are:

Makefile
wch_common.h
wch_devtable.c
wch_main.c
wch_serial.c

When I run **sudo make** followed by any of those file names it says  **make: Nothing to be done for '%filename%'.**
e.g., **make: Nothing to be done for 'wch_main.c'.**

---

### Post by 1fallen on 2024-11-06
> **peyre said:**
> 
When I run **sudo make** followed by any of those file names it says  **make: Nothing to be done for '%filename%'.**
e.g., **make: Nothing to be done for 'wch_main.c'.**

See if this helps with a better description as to why it shows that, can you use "make -d" to see the decisions make is making along the way.

---

### Post by peyre on 2024-11-06
Here you go:

```
GNU Make 4.3
Built for x86_64-pc-linux-gnu
Copyright (C) 1988-2020 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.
Reading makefiles...
Reading makefile 'Makefile'...
Updating makefiles....
 Considering target file 'Makefile'.
  Looking for an implicit rule for 'Makefile'.
  Trying pattern rule with stem 'Makefile'.
  Trying implicit prerequisite 'Makefile.o'.
  Trying pattern rule with stem 'Makefile'.
  Trying implicit prerequisite 'Makefile.c'.
  Trying pattern rule with stem 'Makefile'.
  Trying implicit prerequisite 'Makefile.cc'.
  Trying pattern rule with stem 'Makefile'.
  Trying implicit prerequisite 'Makefile.C'.
  Trying pattern rule with stem 'Makefile'.
  Trying implicit prerequisite 'Makefile.cpp'.
  Trying pattern rule with stem 'Makefile'.
  Trying implicit prerequisite 'Makefile.p'.
  Trying pattern rule with stem 'Makefile'.
  Trying implicit prerequisite 'Makefile.f'.
  Trying pattern rule with stem 'Makefile'.
  Trying implicit prerequisite 'Makefile.F'.
  Trying pattern rule with stem 'Makefile'.
  Trying implicit prerequisite 'Makefile.m'.
  Trying pattern rule with stem 'Makefile'.
  Trying implicit prerequisite 'Makefile.r'.
  Trying pattern rule with stem 'Makefile'.
  Trying implicit prerequisite 'Makefile.s'.
  Trying pattern rule with stem 'Makefile'.
  Trying implicit prerequisite 'Makefile.S'.
  Trying pattern rule with stem 'Makefile'.
  Trying implicit prerequisite 'Makefile.mod'.
  Trying pattern rule with stem 'Makefile'.
  Trying implicit prerequisite 'Makefile.sh'.
  Trying pattern rule with stem 'Makefile'.
  Trying implicit prerequisite 'Makefile,v'.
  Trying pattern rule with stem 'Makefile'.
  Trying implicit prerequisite 'RCS/Makefile,v'.
  Trying pattern rule with stem 'Makefile'.
  Trying implicit prerequisite 'RCS/Makefile'.
  Trying pattern rule with stem 'Makefile'.
  Trying implicit prerequisite 's.Makefile'.
  Trying pattern rule with stem 'Makefile'.
  Trying implicit prerequisite 'SCCS/s.Makefile'.
  Trying pattern rule with stem 'Makefile'.
  Trying implicit prerequisite 'Makefile.o'.
  Looking for a rule with intermediate file 'Makefile.o'.
   Avoiding implicit rule recursion.
   Trying pattern rule with stem 'Makefile'.
   Trying implicit prerequisite 'Makefile.c'.
   Trying pattern rule with stem 'Makefile'.
   Trying implicit prerequisite 'Makefile.cc'.
   Trying pattern rule with stem 'Makefile'.
   Trying implicit prerequisite 'Makefile.C'.
   Trying pattern rule with stem 'Makefile'.
   Trying implicit prerequisite 'Makefile.cpp'.
   Trying pattern rule with stem 'Makefile'.
   Trying implicit prerequisite 'Makefile.p'.
   Trying pattern rule with stem 'Makefile'.
   Trying implicit prerequisite 'Makefile.f'.
   Trying pattern rule with stem 'Makefile'.
   Trying implicit prerequisite 'Makefile.F'.
   Trying pattern rule with stem 'Makefile'.
   Trying implicit prerequisite 'Makefile.m'.
   Trying pattern rule with stem 'Makefile'.
   Trying implicit prerequisite 'Makefile.r'.
   Trying pattern rule with stem 'Makefile'.
   Trying implicit prerequisite 'Makefile.s'.
   Trying pattern rule with stem 'Makefile'.
   Trying implicit prerequisite 'Makefile.S'.
   Trying pattern rule with stem 'Makefile'.
   Trying implicit prerequisite 'Makefile.mod'.
   Trying pattern rule with stem 'Makefile.o'.
   Trying implicit prerequisite 'Makefile.o,v'.
   Trying pattern rule with stem 'Makefile.o'.
   Trying implicit prerequisite 'RCS/Makefile.o,v'.
   Trying pattern rule with stem 'Makefile.o'.
   Trying implicit prerequisite 'RCS/Makefile.o'.
   Trying pattern rule with stem 'Makefile.o'.
   Trying implicit prerequisite 's.Makefile.o'.
   Trying pattern rule with stem 'Makefile.o'.
   Trying implicit prerequisite 'SCCS/s.Makefile.o'.
   Trying pattern rule with stem 'Makefile'.
   Trying implicit prerequisite 'Makefile.c'.
   Looking for a rule with intermediate file 'Makefile.c'.
    Avoiding implicit rule recursion.
    Avoiding implicit rule recursion.
    Trying pattern rule with stem 'Makefile'.
    Trying implicit prerequisite 'Makefile.y'.
    Trying pattern rule with stem 'Makefile'.
    Trying implicit prerequisite 'Makefile.l'.
    Trying pattern rule with stem 'Makefile'.
    Trying implicit prerequisite 'Makefile.w'.
    Trying pattern rule with stem 'Makefile'.
    Trying implicit prerequisite 'Makefile.w'.
    Trying pattern rule with stem 'Makefile.c'.
    Trying implicit prerequisite 'Makefile.c,v'.
    Trying pattern rule with stem 'Makefile.c'.
    Trying implicit prerequisite 'RCS/Makefile.c,v'.
    Trying pattern rule with stem 'Makefile.c'.
    Trying implicit prerequisite 'RCS/Makefile.c'.
    Trying pattern rule with stem 'Makefile.c'.
    Trying implicit prerequisite 's.Makefile.c'.
    Trying pattern rule with stem 'Makefile.c'.
    Trying implicit prerequisite 'SCCS/s.Makefile.c'.
    Trying pattern rule with stem 'Makefile'.
    Trying implicit prerequisite 'Makefile.y'.
    Looking for a rule with intermediate file 'Makefile.y'.
     Avoiding implicit rule recursion.
     Avoiding implicit rule recursion.
     Avoiding implicit rule recursion.
     Trying pattern rule with stem 'Makefile.y'.
     Trying implicit prerequisite 'Makefile.y,v'.
     Trying pattern rule with stem 'Makefile.y'.
     Trying implicit prerequisite 'RCS/Makefile.y,v'.
     Trying pattern rule with stem 'Makefile.y'.
     Trying implicit prerequisite 'RCS/Makefile.y'.
     Trying pattern rule with stem 'Makefile.y'.
     Trying implicit prerequisite 's.Makefile.y'.
     Trying pattern rule with stem 'Makefile.y'.
     Trying implicit prerequisite 'SCCS/s.Makefile.y'.
    Trying pattern rule with stem 'Makefile'.
    Trying implicit prerequisite 'Makefile.l'.
    Looking for a rule with intermediate file 'Makefile.l'.
     Avoiding implicit rule recursion.
     Avoiding implicit rule recursion.
     Avoiding implicit rule recursion.
     Trying pattern rule with stem 'Makefile.l'.
     Trying implicit prerequisite 'Makefile.l,v'.
     Trying pattern rule with stem 'Makefile.l'.
     Trying implicit prerequisite 'RCS/Makefile.l,v'.
     Trying pattern rule with stem 'Makefile.l'.
     Trying implicit prerequisite 'RCS/Makefile.l'.
     Trying pattern rule with stem 'Makefile.l'.
     Trying implicit prerequisite 's.Makefile.l'.
     Trying pattern rule with stem 'Makefile.l'.
     Trying implicit prerequisite 'SCCS/s.Makefile.l'.
    Trying pattern rule with stem 'Makefile'.
    Trying implicit prerequisite 'Makefile.w'.
    Looking for a rule with intermediate file 'Makefile.w'.
     Avoiding implicit rule recursion.
     Avoiding implicit rule recursion.
     Avoiding implicit rule recursion.
     Trying pattern rule with stem 'Makefile.w'.
     Trying implicit prerequisite 'Makefile.w,v'.
     Trying pattern rule with stem 'Makefile.w'.
     Trying implicit prerequisite 'RCS/Makefile.w,v'.
     Trying pattern rule with stem 'Makefile.w'.
     Trying implicit prerequisite 'RCS/Makefile.w'.
     Trying pattern rule with stem 'Makefile.w'.
     Trying implicit prerequisite 's.Makefile.w'.
     Trying pattern rule with stem 'Makefile.w'.
     Trying implicit prerequisite 'SCCS/s.Makefile.w'.
    Trying pattern rule with stem 'Makefile'.
    Rejecting impossible implicit prerequisite 'Makefile.w'.
   Trying pattern rule with stem 'Makefile'.
   Trying implicit prerequisite 'Makefile.cc'.
   Looking for a rule with intermediate file 'Makefile.cc'.
    Avoiding implicit rule recursion.
    Avoiding implicit rule recursion.
    Trying pattern rule with stem 'Makefile.cc'.
    Trying implicit prerequisite 'Makefile.cc,v'.
    Trying pattern rule with stem 'Makefile.cc'.
    Trying implicit prerequisite 'RCS/Makefile.cc,v'.
    Trying pattern rule with stem 'Makefile.cc'.
    Trying implicit prerequisite 'RCS/Makefile.cc'.
    Trying pattern rule with stem 'Makefile.cc'.
    Trying implicit prerequisite 's.Makefile.cc'.
    Trying pattern rule with stem 'Makefile.cc'.
    Trying implicit prerequisite 'SCCS/s.Makefile.cc'.
   Trying pattern rule with stem 'Makefile'.
   Trying implicit prerequisite 'Makefile.C'.
   Looking for a rule with intermediate file 'Makefile.C'.
    Avoiding implicit rule recursion.
    Avoiding implicit rule recursion.
    Trying pattern rule with stem 'Makefile.C'.
    Trying implicit prerequisite 'Makefile.C,v'.
    Trying pattern rule with stem 'Makefile.C'.
    Trying implicit prerequisite 'RCS/Makefile.C,v'.
    Trying pattern rule with stem 'Makefile.C'.
    Trying implicit prerequisite 'RCS/Makefile.C'.
    Trying pattern rule with stem 'Makefile.C'.
    Trying implicit prerequisite 's.Makefile.C'.
    Trying pattern rule with stem 'Makefile.C'.
    Trying implicit prerequisite 'SCCS/s.Makefile.C'.
   Trying pattern rule with stem 'Makefile'.
   Trying implicit prerequisite 'Makefile.cpp'.
   Looking for a rule with intermediate file 'Makefile.cpp'.
    Avoiding implicit rule recursion.
    Avoiding implicit rule recursion.
    Trying pattern rule with stem 'Makefile.cpp'.
    Trying implicit prerequisite 'Makefile.cpp,v'.
    Trying pattern rule with stem 'Makefile.cpp'.
    Trying implicit prerequisite 'RCS/Makefile.cpp,v'.
    Trying pattern rule with stem 'Makefile.cpp'.
    Trying implicit prerequisite 'RCS/Makefile.cpp'.
    Trying pattern rule with stem 'Makefile.cpp'.
    Trying implicit prerequisite 's.Makefile.cpp'.
    Trying pattern rule with stem 'Makefile.cpp'.
    Trying implicit prerequisite 'SCCS/s.Makefile.cpp'.
   Trying pattern rule with stem 'Makefile'.
   Trying implicit prerequisite 'Makefile.p'.
   Looking for a rule with intermediate file 'Makefile.p'.
    Avoiding implicit rule recursion.
    Avoiding implicit rule recursion.
    Trying pattern rule with stem 'Makefile'.
    Trying implicit prerequisite 'Makefile.web'.
    Trying pattern rule with stem 'Makefile.p'.
    Trying implicit prerequisite 'Makefile.p,v'.
    Trying pattern rule with stem 'Makefile.p'.
    Trying implicit prerequisite 'RCS/Makefile.p,v'.
    Trying pattern rule with stem 'Makefile.p'.
    Trying implicit prerequisite 'RCS/Makefile.p'.
    Trying pattern rule with stem 'Makefile.p'.
    Trying implicit prerequisite 's.Makefile.p'.
    Trying pattern rule with stem 'Makefile.p'.
    Trying implicit prerequisite 'SCCS/s.Makefile.p'.
    Trying pattern rule with stem 'Makefile'.
    Trying implicit prerequisite 'Makefile.web'.
    Looking for a rule with intermediate file 'Makefile.web'.
     Avoiding implicit rule recursion.
     Avoiding implicit rule recursion.
     Avoiding implicit rule recursion.
     Trying pattern rule with stem 'Makefile.web'.
     Trying implicit prerequisite 'Makefile.web,v'.
     Trying pattern rule with stem 'Makefile.web'.
     Trying implicit prerequisite 'RCS/Makefile.web,v'.
     Trying pattern rule with stem 'Makefile.web'.
     Trying implicit prerequisite 'RCS/Makefile.web'.
     Trying pattern rule with stem 'Makefile.web'.
     Trying implicit prerequisite 's.Makefile.web'.
     Trying pattern rule with stem 'Makefile.web'.
     Trying implicit prerequisite 'SCCS/s.Makefile.web'.
   Trying pattern rule with stem 'Makefile'.
   Trying implicit prerequisite 'Makefile.f'.
   Looking for a rule with intermediate file 'Makefile.f'.
    Avoiding implicit rule recursion.
    Avoiding implicit rule recursion.
    Trying pattern rule with stem 'Makefile'.
    Trying implicit prerequisite 'Makefile.F'.
    Trying pattern rule with stem 'Makefile'.
    Trying implicit prerequisite 'Makefile.r'.
    Trying pattern rule with stem 'Makefile.f'.
    Trying implicit prerequisite 'Makefile.f,v'.
    Trying pattern rule with stem 'Makefile.f'.
    Trying implicit prerequisite 'RCS/Makefile.f,v'.
    Trying pattern rule with stem 'Makefile.f'.
    Trying implicit prerequisite 'RCS/Makefile.f'.
    Trying pattern rule with stem 'Makefile.f'.
    Trying implicit prerequisite 's.Makefile.f'.
    Trying pattern rule with stem 'Makefile.f'.
    Trying implicit prerequisite 'SCCS/s.Makefile.f'.
    Trying pattern rule with stem 'Makefile'.
    Trying implicit prerequisite 'Makefile.F'.
    Looking for a rule with intermediate file 'Makefile.F'.
     Avoiding implicit rule recursion.
     Avoiding implicit rule recursion.
     Avoiding implicit rule recursion.
     Trying pattern rule with stem 'Makefile.F'.
     Trying implicit prerequisite 'Makefile.F,v'.
     Trying pattern rule with stem 'Makefile.F'.
     Trying implicit prerequisite 'RCS/Makefile.F,v'.
     Trying pattern rule with stem 'Makefile.F'.
     Trying implicit prerequisite 'RCS/Makefile.F'.
     Trying pattern rule with stem 'Makefile.F'.
     Trying implicit prerequisite 's.Makefile.F'.
     Trying pattern rule with stem 'Makefile.F'.
     Trying implicit prerequisite 'SCCS/s.Makefile.F'.
    Trying pattern rule with stem 'Makefile'.
    Trying implicit prerequisite 'Makefile.r'.
    Looking for a rule with intermediate file 'Makefile.r'.
     Avoiding implicit rule recursion.
     Avoiding implicit rule recursion.
     Avoiding implicit rule recursion.
     Trying pattern rule with stem 'Makefile'.
     Rejecting impossible implicit prerequisite 'Makefile.l'.
     Trying pattern rule with stem 'Makefile.r'.
     Trying implicit prerequisite 'Makefile.r,v'.
     Trying pattern rule with stem 'Makefile.r'.
     Trying implicit prerequisite 'RCS/Makefile.r,v'.
     Trying pattern rule with stem 'Makefile.r'.
     Trying implicit prerequisite 'RCS/Makefile.r'.
     Trying pattern rule with stem 'Makefile.r'.
     Trying implicit prerequisite 's.Makefile.r'.
     Trying pattern rule with stem 'Makefile.r'.
     Trying implicit prerequisite 'SCCS/s.Makefile.r'.
   Trying pattern rule with stem 'Makefile'.
   Rejecting impossible implicit prerequisite 'Makefile.F'.
   Trying pattern rule with stem 'Makefile'.
   Trying implicit prerequisite 'Makefile.m'.
   Looking for a rule with intermediate file 'Makefile.m'.
    Avoiding implicit rule recursion.
    Avoiding implicit rule recursion.
    Trying pattern rule with stem 'Makefile'.
    Trying implicit prerequisite 'Makefile.ym'.
    Trying pattern rule with stem 'Makefile.m'.
    Trying implicit prerequisite 'Makefile.m,v'.
    Trying pattern rule with stem 'Makefile.m'.
    Trying implicit prerequisite 'RCS/Makefile.m,v'.
    Trying pattern rule with stem 'Makefile.m'.
    Trying implicit prerequisite 'RCS/Makefile.m'.
    Trying pattern rule with stem 'Makefile.m'.
    Trying implicit prerequisite 's.Makefile.m'.
    Trying pattern rule with stem 'Makefile.m'.
    Trying implicit prerequisite 'SCCS/s.Makefile.m'.
    Trying pattern rule with stem 'Makefile'.
    Trying implicit prerequisite 'Makefile.ym'.
    Looking for a rule with intermediate file 'Makefile.ym'.
     Avoiding implicit rule recursion.
     Avoiding implicit rule recursion.
     Avoiding implicit rule recursion.
     Trying pattern rule with stem 'Makefile.ym'.
     Trying implicit prerequisite 'Makefile.ym,v'.
     Trying pattern rule with stem 'Makefile.ym'.
     Trying implicit prerequisite 'RCS/Makefile.ym,v'.
     Trying pattern rule with stem 'Makefile.ym'.
     Trying implicit prerequisite 'RCS/Makefile.ym'.
     Trying pattern rule with stem 'Makefile.ym'.
     Trying implicit prerequisite 's.Makefile.ym'.
     Trying pattern rule with stem 'Makefile.ym'.
     Trying implicit prerequisite 'SCCS/s.Makefile.ym'.
   Trying pattern rule with stem 'Makefile'.
   Rejecting impossible implicit prerequisite 'Makefile.r'.
   Trying pattern rule with stem 'Makefile'.
   Trying implicit prerequisite 'Makefile.s'.
   Looking for a rule with intermediate file 'Makefile.s'.
    Avoiding implicit rule recursion.
    Avoiding implicit rule recursion.
    Trying pattern rule with stem 'Makefile'.
    Trying implicit prerequisite 'Makefile.S'.
    Trying pattern rule with stem 'Makefile.s'.
    Trying implicit prerequisite 'Makefile.s,v'.
    Trying pattern rule with stem 'Makefile.s'.
    Trying implicit prerequisite 'RCS/Makefile.s,v'.
    Trying pattern rule with stem 'Makefile.s'.
    Trying implicit prerequisite 'RCS/Makefile.s'.
    Trying pattern rule with stem 'Makefile.s'.
    Trying implicit prerequisite 's.Makefile.s'.
    Trying pattern rule with stem 'Makefile.s'.
    Trying implicit prerequisite 'SCCS/s.Makefile.s'.
    Trying pattern rule with stem 'Makefile'.
    Trying implicit prerequisite 'Makefile.S'.
    Looking for a rule with intermediate file 'Makefile.S'.
     Avoiding implicit rule recursion.
     Avoiding implicit rule recursion.
     Avoiding implicit rule recursion.
     Trying pattern rule with stem 'Makefile.S'.
     Trying implicit prerequisite 'Makefile.S,v'.
     Trying pattern rule with stem 'Makefile.S'.
     Trying implicit prerequisite 'RCS/Makefile.S,v'.
     Trying pattern rule with stem 'Makefile.S'.
     Trying implicit prerequisite 'RCS/Makefile.S'.
     Trying pattern rule with stem 'Makefile.S'.
     Trying implicit prerequisite 's.Makefile.S'.
     Trying pattern rule with stem 'Makefile.S'.
     Trying implicit prerequisite 'SCCS/s.Makefile.S'.
   Trying pattern rule with stem 'Makefile'.
   Rejecting impossible implicit prerequisite 'Makefile.S'.
   Trying pattern rule with stem 'Makefile'.
   Trying implicit prerequisite 'Makefile.mod'.
   Looking for a rule with intermediate file 'Makefile.mod'.
    Avoiding implicit rule recursion.
    Avoiding implicit rule recursion.
    Trying pattern rule with stem 'Makefile.mod'.
    Trying implicit prerequisite 'Makefile.mod,v'.
    Trying pattern rule with stem 'Makefile.mod'.
    Trying implicit prerequisite 'RCS/Makefile.mod,v'.
    Trying pattern rule with stem 'Makefile.mod'.
    Trying implicit prerequisite 'RCS/Makefile.mod'.
    Trying pattern rule with stem 'Makefile.mod'.
    Trying implicit prerequisite 's.Makefile.mod'.
    Trying pattern rule with stem 'Makefile.mod'.
    Trying implicit prerequisite 'SCCS/s.Makefile.mod'.
  Trying pattern rule with stem 'Makefile'.
  Rejecting impossible implicit prerequisite 'Makefile.c'.
  Trying pattern rule with stem 'Makefile'.
  Rejecting impossible implicit prerequisite 'Makefile.cc'.
  Trying pattern rule with stem 'Makefile'.
  Rejecting impossible implicit prerequisite 'Makefile.C'.
  Trying pattern rule with stem 'Makefile'.
  Rejecting impossible implicit prerequisite 'Makefile.cpp'.
  Trying pattern rule with stem 'Makefile'.
  Rejecting impossible implicit prerequisite 'Makefile.p'.
  Trying pattern rule with stem 'Makefile'.
  Rejecting impossible implicit prerequisite 'Makefile.f'.
  Trying pattern rule with stem 'Makefile'.
  Rejecting impossible implicit prerequisite 'Makefile.F'.
  Trying pattern rule with stem 'Makefile'.
  Rejecting impossible implicit prerequisite 'Makefile.m'.
  Trying pattern rule with stem 'Makefile'.
  Rejecting impossible implicit prerequisite 'Makefile.r'.
  Trying pattern rule with stem 'Makefile'.
  Rejecting impossible implicit prerequisite 'Makefile.s'.
  Trying pattern rule with stem 'Makefile'.
  Rejecting impossible implicit prerequisite 'Makefile.S'.
  Trying pattern rule with stem 'Makefile'.
  Rejecting impossible implicit prerequisite 'Makefile.mod'.
  Trying pattern rule with stem 'Makefile'.
  Trying implicit prerequisite 'Makefile.sh'.
  Looking for a rule with intermediate file 'Makefile.sh'.
   Avoiding implicit rule recursion.
   Trying pattern rule with stem 'Makefile.sh'.
   Trying implicit prerequisite 'Makefile.sh,v'.
   Trying pattern rule with stem 'Makefile.sh'.
   Trying implicit prerequisite 'RCS/Makefile.sh,v'.
   Trying pattern rule with stem 'Makefile.sh'.
   Trying implicit prerequisite 'RCS/Makefile.sh'.
   Trying pattern rule with stem 'Makefile.sh'.
   Trying implicit prerequisite 's.Makefile.sh'.
   Trying pattern rule with stem 'Makefile.sh'.
   Trying implicit prerequisite 'SCCS/s.Makefile.sh'.
  No implicit rule found for 'Makefile'.
  Finished prerequisites of target file 'Makefile'.
 No need to remake target 'Makefile'.
Updating goal targets....
Considering target file 'wch_main.c'.
 Looking for an implicit rule for 'wch_main.c'.
 Trying pattern rule with stem 'wch_main'.
 Trying implicit prerequisite 'wch_main.y'.
 Trying pattern rule with stem 'wch_main'.
 Trying implicit prerequisite 'wch_main.l'.
 Trying pattern rule with stem 'wch_main'.
 Trying implicit prerequisite 'wch_main.w'.
 Trying pattern rule with stem 'wch_main'.
 Trying implicit prerequisite 'wch_main.w'.
 Trying pattern rule with stem 'wch_main.c'.
 Trying implicit prerequisite 'wch_main.c,v'.
 Trying pattern rule with stem 'wch_main.c'.
 Trying implicit prerequisite 'RCS/wch_main.c,v'.
 Trying pattern rule with stem 'wch_main.c'.
 Trying implicit prerequisite 'RCS/wch_main.c'.
 Trying pattern rule with stem 'wch_main.c'.
 Trying implicit prerequisite 's.wch_main.c'.
 Trying pattern rule with stem 'wch_main.c'.
 Trying implicit prerequisite 'SCCS/s.wch_main.c'.
 Trying pattern rule with stem 'wch_main'.
 Trying implicit prerequisite 'wch_main.y'.
 Looking for a rule with intermediate file 'wch_main.y'.
  Avoiding implicit rule recursion.
  Trying pattern rule with stem 'wch_main.y'.
  Trying implicit prerequisite 'wch_main.y,v'.
  Trying pattern rule with stem 'wch_main.y'.
  Trying implicit prerequisite 'RCS/wch_main.y,v'.
  Trying pattern rule with stem 'wch_main.y'.
  Trying implicit prerequisite 'RCS/wch_main.y'.
  Trying pattern rule with stem 'wch_main.y'.
  Trying implicit prerequisite 's.wch_main.y'.
  Trying pattern rule with stem 'wch_main.y'.
  Trying implicit prerequisite 'SCCS/s.wch_main.y'.
 Trying pattern rule with stem 'wch_main'.
 Trying implicit prerequisite 'wch_main.l'.
 Looking for a rule with intermediate file 'wch_main.l'.
  Avoiding implicit rule recursion.
  Trying pattern rule with stem 'wch_main.l'.
  Trying implicit prerequisite 'wch_main.l,v'.
  Trying pattern rule with stem 'wch_main.l'.
  Trying implicit prerequisite 'RCS/wch_main.l,v'.
  Trying pattern rule with stem 'wch_main.l'.
  Trying implicit prerequisite 'RCS/wch_main.l'.
  Trying pattern rule with stem 'wch_main.l'.
  Trying implicit prerequisite 's.wch_main.l'.
  Trying pattern rule with stem 'wch_main.l'.
  Trying implicit prerequisite 'SCCS/s.wch_main.l'.
 Trying pattern rule with stem 'wch_main'.
 Trying implicit prerequisite 'wch_main.w'.
 Looking for a rule with intermediate file 'wch_main.w'.
  Avoiding implicit rule recursion.
  Trying pattern rule with stem 'wch_main.w'.
  Trying implicit prerequisite 'wch_main.w,v'.
  Trying pattern rule with stem 'wch_main.w'.
  Trying implicit prerequisite 'RCS/wch_main.w,v'.
  Trying pattern rule with stem 'wch_main.w'.
  Trying implicit prerequisite 'RCS/wch_main.w'.
  Trying pattern rule with stem 'wch_main.w'.
  Trying implicit prerequisite 's.wch_main.w'.
  Trying pattern rule with stem 'wch_main.w'.
  Trying implicit prerequisite 'SCCS/s.wch_main.w'.
 Trying pattern rule with stem 'wch_main'.
 Rejecting impossible implicit prerequisite 'wch_main.w'.
 No implicit rule found for 'wch_main.c'.
 Finished prerequisites of target file 'wch_main.c'.
No need to remake target 'wch_main.c'.
make: Nothing to be done for 'wch_main.c'.
```

OTOH, the disk also has a PCIEConfig.exe tool.  Maybe I could run that in Wine.

---

### Post by 1fallen on 2024-11-06
It might be the driver and modules are already installed.
have a look at "man setpci"

If your still on 22.04 Wine might be a possible option IJDK. 24.04 Wine is very buggy ATM.
Sorry peyre, i wish i had something more concrete.

---

### Post by peyre on 2024-11-06
Hey, that config file does run in Wine.  I tested on a laptop so it looks really weird, since the card obvs. isn't plugged into it.   I'll give this a try tonight.

---

### Post by peyre on 2024-11-06
Huh!  No, on my desktop, with a disk in the drive and recognized in Thunar, the tool is still all wonky, with mostly ????? and even weirder symbols in place of text.  I don't know if I'm missing fonts it expects, or what.  I wish I could include a screenshot!  There also doesn't seem to be an option in it for changing the LPT mode.  The box says the card supports SPP, PS2, EPP, and ECP.  The drive must be defaulting to ECP or SPP, because it's running at about that speed, which is about 1/3 the speed of EPP on this thing.

---

### Post by Holger_Gehrke on 2024-11-07
You should have just run 'make' (without sudo, without parameters) in the directory with the 'Makefile' and the source code. This should compile the source files and produce the kernel-module 'wch.ko' as long as the right compiler and any needed header files are available. 

'make' reads 'GNUmakefile', 'makefile', or 'Makefile' to get rules for producing new files from existing files. Any parameters you give it are interpreted as names of targets which need to be defined in the make-file. If you really need to pass the name of a file with rules to 'make' you use one of the option '-f', '--file=', or '--makefile=' with the name of the file to use (e.g. 'make -f ./Makefile'; this is normally only used if there are multiple makefiles for different variants of 'make'). 

After successful compilation running 'sudo make install' should run the target 'install' in the 'Makefile'; I believe 'sudo' will be needed here since it's going to copy files to locations a non-privileged user can't write to. I would **very** carefully read the 'Makefile' to see what it wants to put where.

Holger

---

### Post by grahammechanical on 2024-11-07
>  and even weirder symbols in place of text.  I don't know if I'm missing fonts it expects

Applications run in Wine use Microsoft True Type fonts. As does Windows itself. Cannot use standard fonts installed in Linux distributions. You need to install Microsoft core fonts. To do that we install an installer program.

[https://itsfoss.com/install-microsoft-fonts-ubuntu/](https://itsfoss.com/install-microsoft-fonts-ubuntu/)

We must accept the EULA - use tab to highlight the box to accept the EULA.

Regards

---

### Post by peyre on 2024-11-07
> **Holger_Gehrke said:**
> You should have just run 'make' (without sudo, without parameters) in the directory with the 'Makefile' and the source code. This should compile the source files and produce the kernel-module 'wch.ko' as long as the right compiler and any needed header files are available. 

'make' reads 'GNUmakefile', 'makefile', or 'Makefile' to get rules for producing new files from existing files. Any parameters you give it are interpreted as names of targets which need to be defined in the make-file. If you really need to pass the name of a file with rules to 'make' you use one of the option '-f', '--file=', or '--makefile=' with the name of the file to use (e.g. 'make -f ./Makefile'; this is normally only used if there are multiple makefiles for different variants of 'make'). 

After successful compilation running 'sudo make install' should run the target 'install' in the 'Makefile'; I believe 'sudo' will be needed here since it's going to copy files to locations a non-privileged user can't write to. I would **very** carefully read the 'Makefile' to see what it wants to put where.

I did try that.  **make** still returns "Nothing to be done for '%filename%'."  **make install** returns "make: *** No rule to make target 'install'. Stop."  Maybe the Linux installer is just faulty?  I wouldn't be surprised if the Linux support it touts on the box is slipshod.

---

### Post by peyre on 2024-11-07
> **grahammechanical said:**
> Applications run in Wine use Microsoft True Type fonts. As does Windows itself. Cannot use standard fonts installed in Linux distributions. You need to install Microsoft core fonts. To do that we install an installer program.

[https://itsfoss.com/install-microsoft-fonts-ubuntu/](https://itsfoss.com/install-microsoft-fonts-ubuntu/)

We must accept the EULA - use tab to highlight the box to accept the EULA.

Regards

Oh yeah, should've thought of that.  I've installed corefonts in Winetricks, but it still looks the same.  Is there something else I could use?

I *so* wish I could attach images from file rather than by URL.

Incidentally, when I run wine %filename%, it gives:
```
0124:err:ntoskrnl:dispatch_irp dispatch routine returned 0 but didn't complete the IRP
```

Then when I click on the button in there to **ReadEEPROM**:
```
wine: Call from 7B662597 to unimplemented function hal.dll.HalSetBusDataByOffset, aborting
wine: Unimplemented function hal.dll.HalSetBusDataByOffset called at address 7B662597 (thread 0124), starting debugger...
wine: Call from 7B662597 to unimplemented function hal.dll.HalSetBusDataByOffset, aborting
```

Hey, maybe I should boot with a Windows live disk and see if it runs correctly.

Edit:  I just tried this on my spare laptop, and sure enough it looks the same.  Must be that the config tool is worthless to begin with!

---

### Post by peyre on 2024-11-07
Is there a native Linux means of configuring something like this?  I just want to set it to EPP mode.  In Windows, for instance, Device Manager lets you get properties on a device and set certain settings.  Incidentally, lspci recognizes this card as:

```
Serial controller: Nanjing Qinheng Microelectronics Co., Ltd. CH382L PCIe Parallel Port Adapter (rev 10)
```

I tried installing **hardinfo**.  Good news, it shows things in a nice GUI reminiscent of Device Manager.  Bad news, it looks to be read-only, just informational.  It also doesn't show any of the SPP/ECP/EPP settings. :(

---

