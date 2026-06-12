---
title: "problems with bzImage"
date: 2009-08-12
forum: Installation &amp; Upgrades
---

### Post by kingos82 on 2009-08-12
Hi I am trying to compile a new kernel (2.6.9) so that I can install rtlinux however when I run sudo make bzImage I get the following error:

include/asm/mpspec_def.h:78: warning: 'packed' attribute ignored for field of type 'unsigned char[6]'
arch/i386/kernel/process.c: In function 'show_regs':
arch/i386/kernel/process.c:265: warning: pointer targets in passing argument 2 of 'show_trace' differ in signedness
arch/i386/kernel/process.c: At top level:
arch/i386/kernel/process.c:531: error: redefinition of 'handle_io_bitmap'
arch/i386/kernel/process.c:440: error: previous definition of 'handle_io_bitmap' was here
make[1]: *** [arch/i386/kernel/process.o] Error 1
make: *** [arch/i386/kernel] Error 2



I can't find any solution for it googling up the errors (could it be that I am the first one running into this problem?) also I am using kubuntu 9.04 with KDE 3.5 and I did install the compatible rtlinux patch and the correction patch linux-2.6-seg-5.patch.

Also, I am using gcc 4.3.3 because it doesn't let me compile with the recommended 3.4.6 version.

I am pretty lost and would appericiate any guidance in the issue

thank you very much

Nadav

---

