---
title: "Accidentally installed cdrtools beta on Ubuntu"
date: 2009-03-01
forum: Installation &amp; Upgrades
---

### Post by joshaman on 2009-03-01
I accidentally installed cdrtools 2.01.01 on Ubuntu using the "make" command.  I'm completely new to Linux.  Can someone please tell me how to remove it?

---

### Post by cariboo on 2009-03-01
if you still have the source directory, go into the directory and type:

```
make uninstall
```

Jim

---

### Post by joshaman on 2009-03-01
thanks for the reply.  i'm getting

```
~/Desktop/cdrtools-2.01.01$ make uninstall
		W A R N I N G	Messages like:

gmake[2]: Entering directory `/tmp/cdrtools-2.01/libschily'
../RULES/r-gmake.dep:76: OBJ/<arch-dir>/cvmod.d: No such file or directory
../RULES/r-gmake.dep:76: OBJ/<arch-dir>/dat.d: No such file or directory
../RULES/r-gmake.dep:76: OBJ/<arch-dir>/fcons.d: No such file or directory
../RULES/r-gmake.dep:76: OBJ/<arch-dir>/fdown.d: No such file or directory
../RULES/r-gmake.dep:76: OBJ/<arch-dir>/fdup.d: No such file or directory
../RULES/r-gmake.dep:76: OBJ/<arch-dir>/ffileread.d: No such file or directory
../RULES/r-gmake.dep:76: OBJ/<arch-dir>/ffilewrite.d: No such file or directory
../RULES/r-gmake.dep:76: OBJ/<arch-dir>/fgetline.d: No such file or directory
../RULES/r-gmake.dep:76: OBJ/<arch-dir>/fgetstr.d: No such file or directory
../RULES/r-gmake.dep:76: OBJ/<arch-dir>/file_raise.d: No such file or directory
../RULES/r-gmake.dep:76: OBJ/<arch-dir>/fileclose.d: No such file or directory
....

are caused by a GNU make bug and not by the Schily makefile system.

The related bug has been reported to the GNU make maintainers in 1998 but
as the bug has not yet been fixed, it seems that GNU make is unmaintained :-(
A working highly portable make program is at ftp://ftp.berlios.de/pub/smake
make: *** No rule to make target `uninstall'.  Stop.
```

I guess I can try using smake.. or will it only work had I used it to install also?

---

### Post by joshaman on 2009-03-02
Removed

---

