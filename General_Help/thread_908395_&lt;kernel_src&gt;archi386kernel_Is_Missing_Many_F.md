---
title: "&lt;kernel src&gt;/arch/i386/kernel Is Missing Many Files"
date: 2008-09-02
forum: General Help
---

### Post by kuloch on 2008-09-02
I'm getting the following error when I try to 'make prepare' (via 'sudo make -I/usr/include prepare') my kernel source:
```
No rule to make target `arch/x86/kernel/asm-offsets.c', needed by `arch/x86/kernel/asm-offsets.s'.
```
The problem is that the target (asm-offsets.c) - along with a whole host of other files - is not there.  Comparing what I have to what [it seems I should have]("http://www.linuxhq.com/kernel/v2.6/24/arch/x86/kernel/index.html"), I'm short quite a lot of files there.  My arch/x86/kernel folder only has the 3 Makefiles and the acpi and cpu folders.  None of the many .c files listed are present on my system.

Any idea how I can populate this folder?  I'd even be up for copying a tarball's contents into it.  I just don't want to have to manually copy/paste the contents of each file, name each file, then copy them all over.  And I suspect that's not wise in the first place.

**EDIT** Sorry, the title should read "x86" instead of "i386".  I don't even have the i386 folder in arch, as I assume it was merged into x86.

---

### Post by kuloch on 2008-09-03
Nevermind.  I didn't even notice that the folder was 'kernel-headers-...' instead of 'kernel-source...'.  I just assumed that /usr/src would have all the source in it.  I downloaded a source tarball, and it now works just fine.

---

