---
title: "Nvidia a7n8x sound"
date: 2005-01-12
forum: Installation &amp; Upgrades
---

### Post by CompShrink on 2005-01-12
I have an nvidia a7n8x, and I can't get the shell script or the source code to work.

Heres the messages i get when I try to compile, any ideas on what i should install/configure:

```
root@dynamic-141-079:/home/mike/nforce # make
make -C  nvnet
make[1]: Entering directory `/home/mike/nforce/nvnet'
cc -c -Wall -DLINUX -DMODULE -DEXPORT_SYMTAB -D__KERNEL__ -O -Wstrict-prototypes -DCONFIG_PM  -fno-strict-aliasing -mpreferred-stack-boundary=2 -march=i686 -falign-functions=4 -DMODULE -I/usr/src/linux-2.6.8.1/include   nvnet.c
In file included from /usr/include/asm/smp.h:18,
                 from /usr/include/linux/smp.h:17,
                 from /usr/include/linux/sched.h:23,
                 from /usr/include/linux/module.h:10,
                 from nvnet.h:20,
                 from nvnet.c:21:
/usr/include/asm/mpspec.h:6:25: mach_mpspec.h: No such file or directory
In file included from /usr/include/asm/smp.h:18,
                 from /usr/include/linux/smp.h:17,
                 from /usr/include/linux/sched.h:23,
                 from /usr/include/linux/module.h:10,
                 from nvnet.h:20,
                 from nvnet.c:21:
/usr/include/asm/mpspec.h:8: error: `MAX_MP_BUSSES' undeclared here (not in a function)
/usr/include/asm/mpspec.h:9: error: `MAX_MP_BUSSES' undeclared here (not in a function)
/usr/include/asm/mpspec.h:10: error: `MAX_MP_BUSSES' undeclared here (not in a function)
/usr/include/asm/mpspec.h:12: error: `MAX_MP_BUSSES' undeclared here (not in a function)
/usr/include/asm/mpspec.h:19: error: `MAX_APICS' undeclared here (not in a function)
/usr/include/asm/mpspec.h:20: error: `MAX_MP_BUSSES' undeclared here (not in a function)
/usr/include/asm/mpspec.h:20: error: conflicting types for `mp_bus_id_to_type'
/usr/include/asm/mpspec.h:8: error: previous declaration of `mp_bus_id_to_type'
/usr/include/asm/mpspec.h:22: error: `MAX_IRQ_SOURCES' undeclared here (not in a function)
/usr/include/asm/mpspec.h:24: error: `MAX_MP_BUSSES' undeclared here (not in a function)
/usr/include/asm/mpspec.h:24: error: conflicting types for `mp_bus_id_to_pci_bus'
/usr/include/asm/mpspec.h:12: error: previous declaration of `mp_bus_id_to_pci_bus'
/usr/include/asm/mpspec.h:54: error: `MAX_APICS' undeclared here (not in a function)
In file included from /usr/include/asm/smp.h:20,
                 from /usr/include/linux/smp.h:17,
                 from /usr/include/linux/sched.h:23,
                 from /usr/include/linux/module.h:10,
                 from nvnet.h:20,
                 from nvnet.c:21:
/usr/include/asm/io_apic.h:120: error: `MAX_IRQ_SOURCES' undeclared here (not in a function)
/usr/include/asm/io_apic.h:120: error: conflicting types for `mp_irqs'
/usr/include/asm/mpspec.h:22: error: previous declaration of `mp_irqs'
In file included from /usr/include/linux/smp.h:17,
                 from /usr/include/linux/sched.h:23,
                 from /usr/include/linux/module.h:10,
                 from nvnet.h:20,
                 from nvnet.c:21:
/usr/include/asm/smp.h:73:26: mach_apicdef.h: No such file or directory
In file included from /usr/include/linux/irq.h:20,
                 from /usr/include/asm/hardirq.h:6,
                 from /usr/include/linux/interrupt.h:11,
                 from nvnet.h:30,
                 from nvnet.c:21:
/usr/include/asm/irq.h:16:25: irq_vectors.h: No such file or directory
In file included from /usr/include/asm/hardirq.h:6,
                 from /usr/include/linux/interrupt.h:11,
                 from nvnet.h:30,
                 from nvnet.c:21:
/usr/include/linux/irq.h:70: error: `NR_IRQS' undeclared here (not in a function)
In file included from /usr/include/linux/irq.h:72,
                 from /usr/include/asm/hardirq.h:6,
                 from /usr/include/linux/interrupt.h:11,
                 from nvnet.h:30,
                 from nvnet.c:21:
/usr/include/asm/hw_irq.h:28: error: `NR_IRQS' undeclared here (not in a function)
/usr/include/asm/hw_irq.h:31: error: `NR_IRQS' undeclared here (not in a function)
nvnet.c: In function `nvnet_open':
nvnet.c:735: warning: passing arg 2 of `request_irq' from incompatible pointer type
nvnet.c: In function `nvnet_remove':
nvnet.c:1248: error: structure has no member named `driver_data'
make[1]: *** [nvnet.o] Error 1
make[1]: Leaving directory `/home/mike/nforce/nvnet'
make: *** [nvnet_make] Error 2
```

---

### Post by komputes on 2007-12-23
Do you still have the URL for that nforce script?

---

