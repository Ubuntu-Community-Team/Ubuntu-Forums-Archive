---
title: "Intel HaM driver installing errors"
date: 2007-09-24
forum: Hardware &amp; Laptops
---

### Post by ibbiprince on 2007-09-24
I got an Intel HaM modem that contained a linux driver in its Disc

When i Try to install it it give some error..

It works well when i type make clean

But When i type make Install it gives this error:

> cd coredrv; make ham;
make[1]: Entering directory `/home/asad/412-2/coredrv'
cc -DLINUX -Wall -O -I /usr/src/linux/include -I../inc    -c -o coredrv.o coredr v.c
In file included from ../inc/hamdefs.h:47,
                 from ../inc/hamcore.h:39,
                 from coredrv.c:33:
/usr/include/linux/config.h:1:2: error: #error "Compilation aborted. Please read  the FAQ for linux-libc-headers package."
/usr/include/linux/config.h:2:2: error: #error "(can be found at [http://ep09.pld](http://ep09.pld) -linux.org/~mmazur/linux-libc-headers/doc/)"
coredrv.c:34:25: error: linux/delay.h: No such file or directory
In file included from /usr/include/linux/sched.h:16,
                 from coredrv.c:35:
/usr/include/linux/signal.h:2:2: warning: #warning "You should include <signal.h >. This time I will do it for you."
In file included from /usr/include/linux/resource.h:4,
                 from /usr/include/linux/sched.h:79,
                 from coredrv.c:35:
/usr/include/linux/time.h:9: error: redefinition of â€˜struct timespecâ€™
/usr/include/linux/time.h:15: error: redefinition of â€˜struct timevalâ€™
/usr/include/linux/time.h:20: error: redefinition of â€˜struct timezoneâ€™
/usr/include/linux/time.h:47: error: redefinition of â€˜struct itimervalâ€™
In file included from coredrv.c:36:
/usr/include/linux/proc_fs.h:4:24: error: linux/slab.h: No such file or director y
In file included from coredrv.c:36:
/usr/include/linux/proc_fs.h:245: error: field â€˜vfs_inodeâ€™ has incomplete type
/usr/include/linux/proc_fs.h: In function â€˜PROC_Iâ€™:
/usr/include/linux/proc_fs.h:250: error: syntax error before â€˜structâ€™
In file included from coredrv.c:37:
/usr/include/linux/module.h: At top level:
/usr/include/linux/module.h:41: error: field â€˜attrâ€™ has incomplete type
/usr/include/linux/module.h:49: error: field â€˜kobjâ€™ has incomplete type
In file included from /usr/include/asm/irq.h:11,
                 from coredrv.c:40:
/usr/include/asm-i386/irq.h:15:25: error: irq_vectors.h: No such file or directo ry
/usr/include/asm-i386/irq.h:16:29: error: asm/thread_info.h: No such file or dir ectory
coredrv.c:48: warning: type defaults to â€˜intâ€™ in declaration of â€˜EXPORT_SYMBOL_N OVERSâ€™
coredrv.c:48: warning: parameter names (without types) in function declaration
coredrv.c:48: warning: data definition has no type or storage class
coredrv.c:49: warning: type defaults to â€˜intâ€™ in declaration of â€˜EXPORT_SYMBOL_N OVERSâ€™
coredrv.c:49: warning: parameter names (without types) in function declaration
coredrv.c:49: warning: data definition has no type or storage class
coredrv.c:50: warning: type defaults to â€˜intâ€™ in declaration of â€˜EXPORT_SYMBOL_N OVERSâ€™
coredrv.c:50: warning: parameter names (without types) in function declaration
coredrv.c:50: warning: data definition has no type or storage class
coredrv.c:51: warning: type defaults to â€˜intâ€™ in declaration of â€˜EXPORT_SYMBOL_N OVERSâ€™
coredrv.c:51: warning: parameter names (without types) in function declaration
coredrv.c:51: warning: data definition has no type or storage class
coredrv.c:52: warning: type defaults to â€˜intâ€™ in declaration of â€˜EXPORT_SYMBOL_N OVERSâ€™
coredrv.c:52: warning: parameter names (without types) in function declaration
coredrv.c:52: warning: data definition has no type or storage class
coredrv.c:53: warning: type defaults to â€˜intâ€™ in declaration of â€˜EXPORT_SYMBOL_N OVERSâ€™
coredrv.c:53: warning: parameter names (without types) in function declaration
coredrv.c:53: warning: data definition has no type or storage class
coredrv.c:54: warning: type defaults to â€˜intâ€™ in declaration of â€˜EXPORT_SYMBOL_N OVERSâ€™
coredrv.c:54: warning: parameter names (without types) in function declaration
coredrv.c:54: warning: data definition has no type or storage class
coredrv.c:55: warning: type defaults to â€˜intâ€™ in declaration of â€˜EXPORT_SYMBOL_N OVERSâ€™
coredrv.c:55: warning: parameter names (without types) in function declaration
coredrv.c:55: warning: data definition has no type or storage class
coredrv.c:56: warning: type defaults to â€˜intâ€™ in declaration of â€˜EXPORT_SYMBOL_N OVERSâ€™
coredrv.c:56: warning: parameter names (without types) in function declaration
coredrv.c:56: warning: data definition has no type or storage class
coredrv.c:57: warning: type defaults to â€˜intâ€™ in declaration of â€˜EXPORT_SYMBOL_N OVERSâ€™
coredrv.c:57: warning: parameter names (without types) in function declaration
coredrv.c:57: warning: data definition has no type or storage class
coredrv.c:58: warning: type defaults to â€˜intâ€™ in declaration of â€˜EXPORT_SYMBOL_N OVERSâ€™
coredrv.c:58: warning: parameter names (without types) in function declaration
coredrv.c:58: warning: data definition has no type or storage class
coredrv.c:59: warning: type defaults to â€˜intâ€™ in declaration of â€˜EXPORT_SYMBOL_N OVERSâ€™
coredrv.c:59: warning: parameter names (without types) in function declaration
coredrv.c:59: warning: data definition has no type or storage class
coredrv.c:60: warning: type defaults to â€˜intâ€™ in declaration of â€˜EXPORT_SYMBOL_N OVERSâ€™
coredrv.c:60: warning: parameter names (without types) in function declaration
coredrv.c:60: warning: data definition has no type or storage class
coredrv.c:61: warning: type defaults to â€˜intâ€™ in declaration of â€˜EXPORT_SYMBOL_N OVERSâ€™
coredrv.c:61: warning: parameter names (without types) in function declaration
coredrv.c:61: warning: data definition has no type or storage class
coredrv.c:62: warning: type defaults to â€˜intâ€™ in declaration of â€˜EXPORT_SYMBOL_N OVERSâ€™
coredrv.c:62: warning: parameter names (without types) in function declaration
coredrv.c:62: warning: data definition has no type or storage class
coredrv.c:63: warning: type defaults to â€˜intâ€™ in declaration of â€˜EXPORT_SYMBOL_N OVERSâ€™
coredrv.c:63: warning: parameter names (without types) in function declaration
coredrv.c:63: warning: data definition has no type or storage class
coredrv.c:64: warning: type defaults to â€˜intâ€™ in declaration of â€˜EXPORT_SYMBOL_N OVERSâ€™
coredrv.c:64: warning: parameter names (without types) in function declaration
coredrv.c:64: warning: data definition has no type or storage class
coredrv.c:65: warning: type defaults to â€˜intâ€™ in declaration of â€˜EXPORT_SYMBOL_N OVERSâ€™
coredrv.c:65: warning: parameter names (without types) in function declaration
coredrv.c:65: warning: data definition has no type or storage class
coredrv.c:66: warning: type defaults to â€˜intâ€™ in declaration of â€˜EXPORT_SYMBOL_N OVERSâ€™
coredrv.c:66: warning: parameter names (without types) in function declaration
coredrv.c:66: warning: data definition has no type or storage class
coredrv.c:67: warning: type defaults to â€˜intâ€™ in declaration of â€˜EXPORT_SYMBOL_N OVERSâ€™
coredrv.c:67: warning: parameter names (without types) in function declaration
coredrv.c:67: warning: data definition has no type or storage class
coredrv.c:68: warning: type defaults to â€˜intâ€™ in declaration of â€˜EXPORT_SYMBOL_N OVERSâ€™
coredrv.c:68: warning: parameter names (without types) in function declaration
coredrv.c:68: warning: data definition has no type or storage class
coredrv.c:69: warning: type defaults to â€˜intâ€™ in declaration of â€˜EXPORT_SYMBOL_N OVERSâ€™
coredrv.c:69: warning: parameter names (without types) in function declaration
coredrv.c:69: warning: data definition has no type or storage class
coredrv.c:70: warning: type defaults to â€˜intâ€™ in declaration of â€˜EXPORT_SYMBOL_N OVERSâ€™
coredrv.c:70: warning: parameter names (without types) in function declaration
coredrv.c:70: warning: data definition has no type or storage class
coredrv.c:105: warning: type defaults to â€˜intâ€™ in declaration of â€˜DECLARE_MUTEXâ€™
coredrv.c:105: warning: parameter names (without types) in function declaration
coredrv.c:105: warning: data definition has no type or storage class
coredrv.c:106: warning: type defaults to â€˜intâ€™ in declaration of â€˜DECLARE_WAIT_Q UEUE_HEADâ€™
coredrv.c:106: warning: parameter names (without types) in function declaration
coredrv.c:106: warning: data definition has no type or storage class
coredrv.c:107: warning: type defaults to â€˜intâ€™ in declaration of â€˜DECLARE_WAIT_Q UEUE_HEADâ€™
coredrv.c:107: warning: parameter names (without types) in function declaration
coredrv.c:107: warning: data definition has no type or storage class
coredrv.c:108: warning: type defaults to â€˜intâ€™ in declaration of â€˜DECLARE_WAIT_Q UEUE_HEADâ€™
coredrv.c:108: warning: parameter names (without types) in function declaration
coredrv.c:108: warning: data definition has no type or storage class
coredrv.c:124: warning: â€˜struct fileâ€™ declared inside parameter list
coredrv.c: In function â€˜create_hamprocâ€™:
coredrv.c:132: error: â€˜S_IFREGâ€™ undeclared (first use in this function)
coredrv.c:132: error: (Each undeclared identifier is reported only once
coredrv.c:132: error: for each function it appears in.)
coredrv.c:132: error: â€˜S_IRUGOâ€™ undeclared (first use in this function)
coredrv.c:135: warning: assignment from incompatible pointer type
coredrv.c: In function â€˜hamcore_initâ€™:
coredrv.c:147: error: â€˜printkâ€™ undeclared (first use in this function)
coredrv.c:148: error: â€˜scheduleâ€™ undeclared (first use in this function)
coredrv.c:149: warning: implicit declaration of function â€˜printkâ€™
coredrv.c:149: error: â€˜KERN_DEBUGâ€™ undeclared (first use in this function)
coredrv.c:149: error: syntax error before string constant
coredrv.c:152: error: â€˜KERN_ALERTâ€™ undeclared (first use in this function)
coredrv.c:152: error: syntax error before string constant
coredrv.c:157: error: syntax error before string constant
coredrv.c:169: error: syntax error before string constant
coredrv.c:179: error: syntax error before string constant
coredrv.c:189: error: syntax error before string constant
coredrv.c:202: error: syntax error before string constant
coredrv.c:211: error: syntax error before string constant
coredrv.c:221: error: syntax error before string constant
coredrv.c:232: error: syntax error before string constant
coredrv.c: In function â€˜init_moduleâ€™:
coredrv.c:243: warning: implicit declaration of function â€˜printkâ€™
coredrv.c: In function â€˜kdelayâ€™:
coredrv.c:257: warning: implicit declaration of function â€˜mdelayâ€™
coredrv.c: In function â€˜kudelayâ€™:
coredrv.c:261: warning: implicit declaration of function â€˜udelayâ€™
coredrv.c: In function â€˜kcliâ€™:
coredrv.c:266: warning: implicit declaration of function â€˜cliâ€™
coredrv.c: In function â€˜ksave_flagsâ€™:
coredrv.c:271: warning: implicit declaration of function â€˜save_flagsâ€™
coredrv.c: In function â€˜krestore_flagsâ€™:
coredrv.c:276: warning: implicit declaration of function â€˜restore_flagsâ€™
coredrv.c: In function â€˜up_exec_reg_semâ€™:
coredrv.c:282: warning: implicit declaration of function â€˜upâ€™
coredrv.c:282: error: â€˜exec_reg_semâ€™ undeclared (first use in this function)
coredrv.c: In function â€˜down_exec_reg_semâ€™:
coredrv.c:287: warning: implicit declaration of function â€˜downâ€™
coredrv.c:287: error: â€˜exec_reg_semâ€™ undeclared (first use in this function)
coredrv.c: In function â€˜wake_up_interruptible_persistWriteQâ€™:
coredrv.c:292: warning: implicit declaration of function â€˜wake_up_interruptibleâ€™
coredrv.c:292: error: â€˜persistWriteQâ€™ undeclared (first use in this function)
coredrv.c: In function â€˜wake_up_interruptible_persistReadQâ€™:
coredrv.c:297: error: â€˜persistReadQâ€™ undeclared (first use in this function)
coredrv.c: In function â€˜interruptible_sleep_on_persistReadQâ€™:
coredrv.c:303: warning: implicit declaration of function â€˜interruptible_sleep_on â€™
coredrv.c:303: error: â€˜persistReadQâ€™ undeclared (first use in this function)
coredrv.c: In function â€˜interruptible_sleep_on_timeout_persistWriteQâ€™:
coredrv.c:310: warning: implicit declaration of function â€˜interruptible_sleep_on _timeoutâ€™
coredrv.c:310: error: â€˜persistWriteQâ€™ undeclared (first use in this function)
coredrv.c: In function â€˜interruptible_sleep_on_timeout_persistReadQâ€™:
coredrv.c:318: error: â€˜persistReadQâ€™ undeclared (first use in this function)
coredrv.c: In function â€˜ham_proc_shutdown_waitâ€™:
coredrv.c:327: error: â€˜currentâ€™ undeclared (first use in this function)
coredrv.c:328: warning: implicit declaration of function â€˜schedule_timeoutâ€™
coredrv.c: In function â€˜kdisable_irqâ€™:
coredrv.c:334: warning: implicit declaration of function â€˜disable_irqâ€™
coredrv.c: In function â€˜kenable_irqâ€™:
coredrv.c:339: warning: implicit declaration of function â€˜enable_irqâ€™
coredrv.c: In function â€˜kCurrentCommâ€™:
coredrv.c:344: error: â€˜currentâ€™ undeclared (first use in this function)
coredrv.c:345: warning: control reaches end of non-void function
make[1]: *** [coredrv.o] Error 1
make[1]: Leaving directory `/home/asad/412-2/coredrv'
make: *** [ham] Error 2
root@AMT-Mainframe:/home/asad/412-2#

Plz help me out...
Thx in advance

---

