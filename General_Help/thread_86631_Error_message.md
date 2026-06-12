---
title: "Error message"
date: 2005-11-05
forum: General Help
---

### Post by Drifter on 2005-11-05
Can anyone tell me what this means and how can I find it to fix it.  I am trying to make the new kernel.

kernel/sched.c:1231: error: redefinition of ‘cache_delay’
kernel/sched.c:1211: error: previous definition of ‘cache_delay’ was here
kernel/sched.c:1238: error: redefinition of ‘preempt’
kernel/sched.c:1218: error: previous definition of ‘preempt’ was here
{standard input}: Assembler messages:
{standard input}:432: Error: symbol `cache_delay' is already defined
make[2]: *** [kernel/sched.o] Error 1
make[1]: *** [kernel] Error 2
make[1]: Leaving directory `/usr/src/linux-2.6.14cK1'
make: *** [stamp-build] Error 2

---

### Post by nightfly on 2005-11-06
This means that the compiler has found errors in the source code. From what I can guess, there is a code duplication somewhere .. like some file is being compiled more than once.

Make sure the source tree you have is 'pristine'. If possible, fetch the tarball for the kernel tarball and overwrite the source tree you have. You can backup your configuration by copying the ".config" file to somewhere from the root of the source tree.

Please note that in addition to compiling the kernel, you will also have to build modules and install them. You will also need to configure the boot loader to be able to boot using the new kernel.

P.S.
I suggest not using the source tarball from kernel.org
It would be better if you used the "stock" kernel source tree from synaptic
It is version 2.6.12 but has some ubuntu patches to enhance scheduling and power support.

---

