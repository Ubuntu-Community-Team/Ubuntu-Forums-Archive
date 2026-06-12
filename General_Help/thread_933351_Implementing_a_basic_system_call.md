---
title: "Implementing a basic system call"
date: 2008-09-29
forum: General Help
---

### Post by phosse1 on 2008-09-29
Hi everyone,

I've got a small problem when I try to implement a 'hello world' system call. I've read the tutorials online aswell as textbooks for references, but when I recompile my kernel, I get an error. 
I've pasted all required info and I'd be greatly appreciative for any assistance.

My System call... outputs 'Hello World'. This file compiles perfectly:
[PHP]
#include </usr/src/linux-source-2.6.24/include/linux/kernel.h>
#include </usr/src/linux-source-2.6.24/include/asm-x86/linkage.h>
asmlinkage (long sys_helloworld())
{
printk("HELLO WORLD!!");
return 1;
}[/PHP]

Defining a new Sys call number in unistd_32.h:
[PHP]
// Location of file: /usr/src/linux/include/asm-x86/unistd_32.h
// BTW I also incremented the __NR_syscalls also
#define __NR_helloworld		325[/PHP]


Now I add an entry into the system call table:
[PHP]// Location of file: /usr/src/linux/arch/x86/kernel/syscall_table_32. 
.long sys_helloworld		/* For the added system call*/ 
[/PHP]

Lastly, In the makefile, I add: [PHP]obj-y := helloworld.o[/PHP]


But when I compile my kernel, I get an error, it compiles for 10-12 minutes before I get this error:
[PHP]arch/x86/kernel/built-in.o: In function `sys_call_table':
(.rodata+0x514): undefined reference to `sys_helloworld'
make[1]: *** [.tmp_vmlinux1] Error 1
make[1]: Leaving directory `/usr/src/linux-source-2.6.24'
make: *** [debian/stamp-build-kernel] Error 2[/PHP]

I would be VERY appreciative if anyone knows where I'm going wrong.

Thanks in advance,
p.

---

