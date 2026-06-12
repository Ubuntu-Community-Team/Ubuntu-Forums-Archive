---
title: "kernel debug problem"
date: 2009-02-27
forum: Illinois Team
---

### Post by anuragccsu on 2009-02-27
Hi All
i am using ubuntu8.10 with kernel 2.6.27 installed in my system.
I've to debug the kernel(for learning purpose) using kgdb, for that i searched on net and found that kgdb is avaliaible only for 2.6.15 kernel source.
so i downloaded 2.6.15 kernel source and put it in my /usr/src directory after that i reffered the link:-
**[COLOR="Blue"]http://beginlinux.wordpress.com/2008/12/03/how-to-compile-an-ubuntu-810-kernel/[/COLOR]**
(i copied the config file from the kernel installed in my machine having kernel 2.6.27)but in the compilatoin it is giving me the error:

include/asm/mpspec_def.h:78: warning: packed attribute ignored for field of type unsigned char[6]
arch/i386/kernel/apic.c: In function smp_apic_timer_interrupt:
arch/i386/kernel/apic.c:1136: sorry, unimplemented: inlining failed in [B][COLOR="Red"]call to smp_local_timer_interrupt: function body not available
arch/i386/kernel/apic.c:1205: sorry, unimplemented: called from here
make[1]: *** [arch/i386/kernel/apic.o] Error 1
make: *** [arch/i386/kernel] Error 2[/COLOR][/B]

so how to work around this problem? plz help.


and one more thing is there any version of kgdb available to debug the 2.6.27 kernel?

thanks

---

### Post by overflow_ on 2009-03-25
> **anuragccsu said:**
> Hi All
i am using ubuntu8.10 with kernel 2.6.27 installed in my system.
I've to debug the kernel(for learning purpose) using kgdb, for that i searched on net and found that kgdb is avaliaible only for 2.6.15 kernel source.
so i downloaded 2.6.15 kernel source and put it in my /usr/src directory after that i reffered the link:-
**[COLOR="Blue"]http://beginlinux.wordpress.com/2008/12/03/how-to-compile-an-ubuntu-810-kernel/[/COLOR]**
(i copied the config file from the kernel installed in my machine having kernel 2.6.27)but in the compilatoin it is giving me the error:

include/asm/mpspec_def.h:78: warning: packed attribute ignored for field of type unsigned char[6]
arch/i386/kernel/apic.c: In function smp_apic_timer_interrupt:
arch/i386/kernel/apic.c:1136: sorry, unimplemented: inlining failed in [B][COLOR="Red"]call to smp_local_timer_interrupt: function body not available
arch/i386/kernel/apic.c:1205: sorry, unimplemented: called from here
make[1]: *** [arch/i386/kernel/apic.o] Error 1
make: *** [arch/i386/kernel] Error 2[/COLOR][/B]

so how to work around this problem? plz help.


and one more thing is there any version of kgdb available to debug the 2.6.27 kernel?

thanks

Hello! I have found the same problem compiling the kernel 2.6.11.12
I have tried also to don't include APIC support in the configuration menu, but without success!

---

### Post by julianelischer on 2009-04-23
While you need 2.6.15 to use the full patches, kgdb is in 2.6.27 that you have by default on your system.

you need boot arguments of kgdboc=ttyS1,115200 for com2 and S0 for com1  of course.

you of course need 2 machines... but I'm sure you know that.

---

