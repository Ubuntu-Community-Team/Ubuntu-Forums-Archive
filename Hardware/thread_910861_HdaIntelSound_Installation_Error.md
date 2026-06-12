---
title: "HdaIntelSound Installation Error"
date: 2008-09-04
forum: Hardware
---

### Post by StandardsDT on 2008-09-04
I'm following the instructions from the following link below

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

to try and get my volume wheel/knob on my laptop working. However when I enter the make command in the terminal I get a bunch of errors towards the end. Here is the output from terminal.

> 

make[1]: Entering directory `/home/dave/Desktop/alsa/alsa-driver-1.0.9/acore'
gcc -D__KERNEL__ -DMODULE=1 -I/home/dave/Desktop/alsa/alsa-driver-1.0.9/include  -I/usr/src/linux-headers-2.6.24-19-generic/include -O2 -mpreferred-stack-boundary=2 -march=i586 -D__SMP__ -DCONFIG_SMP -DLINUX -Wall -Wstrict-prototypes -fomit-frame-pointer -Wno-trigraphs -O2 -fno-strict-aliasing -fno-common -pipe -DALSA_BUILD -nostdinc -iwithprefix include -DMODVERSIONS -include /usr/src/linux-headers-2.6.24-19-generic/include/linux/modversions.h  -DKBUILD_BASENAME=hpetimer   -c -o hpetimer.o hpetimer.c
cc1: error: /usr/src/linux-headers-2.6.24-19-generic/include/linux/modversions.h: No such file or directory
In file included from hpetimer.c:22:
/home/dave/Desktop/alsa/alsa-driver-1.0.9/include/sound/driver.h:29:26: error: linux/config.h: No such file or directory
Assembler messages:
Fatal error: can't create hpetimer.o: Permission denied
In file included from /usr/src/linux-headers-2.6.24-19-generic/include/asm/current_64.h:7,
                 from /usr/src/linux-headers-2.6.24-19-generic/include/asm/current.h:4,
                 from /usr/src/linux-headers-2.6.24-19-generic/include/asm/processor_64.h:17,
                 from /usr/src/linux-headers-2.6.24-19-generic/include/asm/processor.h:4,
                 from /usr/src/linux-headers-2.6.24-19-generic/include/linux/prefetch.h:14,
                 from /usr/src/linux-headers-2.6.24-19-generic/include/linux/list.h:8,
                 from /usr/src/linux-headers-2.6.24-19-generic/include/linux/module.h:9,
                 from /home/dave/Desktop/alsa/alsa-driver-1.0.9/include/adriver.h:45,
                 from /home/dave/Desktop/alsa/alsa-driver-1.0.9/include/sound/driver.h:42,
                 from hpetimer.c:22:
/usr/src/linux-headers-2.6.24-19-generic/include/asm/pda.h:39: error: ‘CONFIG_X86_L1_CACHE_SHIFT’ undeclared here (not in a function)
/usr/src/linux-headers-2.6.24-19-generic/include/asm/pda.h:39: error: requested alignment is not a constant
In file included from /usr/src/linux-headers-2.6.24-19-generic/include/asm/processor_64.h:22,
                 from /usr/src/linux-headers-2.6.24-19-generic/include/asm/processor.h:4,
                 from /usr/src/linux-headers-2.6.24-19-generic/include/linux/prefetch.h:14,
                 from /usr/src/linux-headers-2.6.24-19-generic/include/linux/list.h:8,
                 from /usr/src/linux-headers-2.6.24-19-generic/include/linux/module.h:9,
                 from /home/dave/Desktop/alsa/alsa-driver-1.0.9/include/adriver.h:45,
                 from /home/dave/Desktop/alsa/alsa-driver-1.0.9/include/sound/driver.h:42,
                 from hpetimer.c:22:
/usr/src/linux-headers-2.6.24-19-generic/include/linux/cpumask.h:88: error: ‘CONFIG_NR_CPUS’ undeclared here (not in a function)
In file included from /usr/src/linux-headers-2.6.24-19-generic/include/asm/processor.h:4,
                 from /usr/src/linux-headers-2.6.24-19-generic/include/linux/prefetch.h:14,
                 from /usr/src/linux-headers-2.6.24-19-generic/include/linux/list.h:8,
                 from /usr/src/linux-headers-2.6.24-19-generic/include/linux/module.h:9,
                 from /home/dave/Desktop/alsa/alsa-driver-1.0.9/include/adriver.h:45,
                 from /home/dave/Desktop/alsa/alsa-driver-1.0.9/include/sound/driver.h:42,
                 from hpetimer.c:22:
/usr/src/linux-headers-2.6.24-19-generic/include/asm/processor_64.h:79: error: requested alignment is not a constant
/usr/src/linux-headers-2.6.24-19-generic/include/asm/processor_64.h:200: error: requested alignment is not a constant
In file included from /usr/src/linux-headers-2.6.24-19-generic/include/asm/ptrace.h:35,
                 from /usr/src/linux-headers-2.6.24-19-generic/include/asm/elf.h:8,
                 from /usr/src/linux-headers-2.6.24-19-generic/include/linux/elf.h:6,
                 from /usr/src/linux-headers-2.6.24-19-generic/include/linux/module.h:14,
                 from /home/dave/Desktop/alsa/alsa-driver-1.0.9/include/adriver.h:45,
                 from /home/dave/Desktop/alsa/alsa-driver-1.0.9/include/sound/driver.h:42,
                 from hpetimer.c:22:
/usr/src/linux-headers-2.6.24-19-generic/include/asm/vm86.h:22:1: warning: "VM_MASK" redefined
In file included from /usr/src/linux-headers-2.6.24-19-generic/include/asm/processor.h:4,
                 from /usr/src/linux-headers-2.6.24-19-generic/include/linux/prefetch.h:14,
                 from /usr/src/linux-headers-2.6.24-19-generic/include/linux/list.h:8,
                 from /usr/src/linux-headers-2.6.24-19-generic/include/linux/module.h:9,
                 from /home/dave/Desktop/alsa/alsa-driver-1.0.9/include/adriver.h:45,
                 from /home/dave/Desktop/alsa/alsa-driver-1.0.9/include/sound/driver.h:42,
                 from hpetimer.c:22:
/usr/src/linux-headers-2.6.24-19-generic/include/asm/processor_64.h:29:1: warning: this is the location of the previous definition
In file included from /usr/src/linux-headers-2.6.24-19-generic/include/asm/elf.h:8,
                 from /usr/src/linux-headers-2.6.24-19-generic/include/linux/elf.h:6,
                 from /usr/src/linux-headers-2.6.24-19-generic/include/linux/module.h:14,
                 from /home/dave/Desktop/alsa/alsa-driver-1.0.9/include/adriver.h:45,
                 from /home/dave/Desktop/alsa/alsa-driver-1.0.9/include/sound/driver.h:42,
                 from hpetimer.c:22:
/usr/src/linux-headers-2.6.24-19-generic/include/asm/ptrace.h: In function ‘user_mode’:
/usr/src/linux-headers-2.6.24-19-generic/include/asm/ptrace.h:50: error: ‘SEGMENT_RPL_MASK’ undeclared (first use in this function)
/usr/src/linux-headers-2.6.24-19-generic/include/asm/ptrace.h:50: error: (Each undeclared identifier is reported only once
/usr/src/linux-headers-2.6.24-19-generic/include/asm/ptrace.h:50: error: for each function it appears in.)
/usr/src/linux-headers-2.6.24-19-generic/include/asm/ptrace.h:50: error: ‘USER_RPL’ undeclared (first use in this function)
/usr/src/linux-headers-2.6.24-19-generic/include/asm/ptrace.h: In function ‘user_mode_vm’:
/usr/src/linux-headers-2.6.24-19-generic/include/asm/ptrace.h:54: error: ‘SEGMENT_RPL_MASK’ undeclared (first use in this function)
/usr/src/linux-headers-2.6.24-19-generic/include/asm/ptrace.h:54: error: ‘USER_RPL’ undeclared (first use in this function)
In file included from /usr/src/linux-headers-2.6.24-19-generic/include/linux/gfp.h:4,
                 from /usr/src/linux-headers-2.6.24-19-generic/include/linux/slab.h:14,
                 from /usr/src/linux-headers-2.6.24-19-generic/include/linux/percpu.h:5,
                 from /usr/src/linux-headers-2.6.24-19-generic/include/asm/local_64.h:4,
                 from /usr/src/linux-headers-2.6.24-19-generic/include/asm/local.h:4,
                 from /usr/src/linux-headers-2.6.24-19-generic/include/linux/module.h:19,
                 from /home/dave/Desktop/alsa/alsa-driver-1.0.9/include/adriver.h:45,
                 from /home/dave/Desktop/alsa/alsa-driver-1.0.9/include/sound/driver.h:42,
                 from hpetimer.c:22:
/usr/src/linux-headers-2.6.24-19-generic/include/linux/mmzone.h: At top level:
/usr/src/linux-headers-2.6.24-19-generic/include/linux/mmzone.h:74: error: requested alignment is not a constant
/usr/src/linux-headers-2.6.24-19-generic/include/linux/mmzone.h:124: error: requested alignment is not a constant
/usr/src/linux-headers-2.6.24-19-generic/include/linux/mmzone.h:342: error: requested alignment is not a constant
In file included from /usr/src/linux-headers-2.6.24-19-generic/include/asm/hardirq_64.h:5,
                 from /usr/src/linux-headers-2.6.24-19-generic/include/asm/hardirq.h:4,
                 from /usr/src/linux-headers-2.6.24-19-generic/include/linux/hardirq.h:7,
                 from /usr/src/linux-headers-2.6.24-19-generic/include/linux/interrupt.h:11,
                 from hpetimer.c:26:
/usr/src/linux-headers-2.6.24-19-generic/include/linux/irq.h:178: error: requested alignment is not a constant
In file included from /usr/src/linux-headers-2.6.24-19-generic/include/linux/sched.h:54,
                 from /usr/src/linux-headers-2.6.24-19-generic/include/linux/interrupt.h:12,
                 from hpetimer.c:26:
/usr/src/linux-headers-2.6.24-19-generic/include/linux/jiffies.h:33:3: error: #error You lose.
/usr/src/linux-headers-2.6.24-19-generic/include/linux/jiffies.h:225:31: error: division by zero in #if
/usr/src/linux-headers-2.6.24-19-generic/include/linux/jiffies.h:225:31: error: division by zero in #if
/usr/src/linux-headers-2.6.24-19-generic/include/linux/jiffies.h:225:31: error: division by zero in #if
/usr/src/linux-headers-2.6.24-19-generic/include/linux/jiffies.h:225:31: error: division by zero in #if
/usr/src/linux-headers-2.6.24-19-generic/include/linux/jiffies.h:225:31: error: division by zero in #if
/usr/src/linux-headers-2.6.24-19-generic/include/linux/jiffies.h:225:31: error: division by zero in #if
/usr/src/linux-headers-2.6.24-19-generic/include/linux/jiffies.h:225:31: error: division by zero in #if
/usr/src/linux-headers-2.6.24-19-generic/include/linux/jiffies.h:225:31: error: division by zero in #if
/usr/src/linux-headers-2.6.24-19-generic/include/linux/jiffies.h:225:31: error: division by zero in #if
/usr/src/linux-headers-2.6.24-19-generic/include/linux/jiffies.h:225:31: error: division by zero in #if
/usr/src/linux-headers-2.6.24-19-generic/include/linux/jiffies.h:225:31: error: division by zero in #if
/usr/src/linux-headers-2.6.24-19-generic/include/linux/jiffies.h:225:31: error: division by zero in #if
/usr/src/linux-headers-2.6.24-19-generic/include/linux/jiffies.h:225:31: error: division by zero in #if
/usr/src/linux-headers-2.6.24-19-generic/include/linux/jiffies.h:225:31: error: division by zero in #if
/usr/src/linux-headers-2.6.24-19-generic/include/linux/jiffies.h:225:31: error: division by zero in #if
/usr/src/linux-headers-2.6.24-19-generic/include/linux/jiffies.h:225:31: error: division by zero in #if
In file included from /usr/src/linux-headers-2.6.24-19-generic/include/linux/pid.h:4,
                 from /usr/src/linux-headers-2.6.24-19-generic/include/linux/sched.h:75,
                 from /usr/src/linux-headers-2.6.24-19-generic/include/linux/interrupt.h:12,
                 from hpetimer.c:26:
/usr/src/linux-headers-2.6.24-19-generic/include/linux/rcupdate.h:72: error: requested alignment is not a constant
/usr/src/linux-headers-2.6.24-19-generic/include/linux/rcupdate.h:75: error: requested alignment is not a constant
In file included from /usr/src/linux-headers-2.6.24-19-generic/include/linux/sched.h:78,
                 from /usr/src/linux-headers-2.6.24-19-generic/include/linux/interrupt.h:12,
                 from hpetimer.c:26:
/usr/src/linux-headers-2.6.24-19-generic/include/linux/proportions.h: In function ‘prop_inc_percpu’:
/usr/src/linux-headers-2.6.24-19-generic/include/linux/proportions.h:75: warning: implicit declaration of function ‘local_irq_save’
/usr/src/linux-headers-2.6.24-19-generic/include/linux/proportions.h:77: warning: implicit declaration of function ‘local_irq_restore’
In file included from /usr/src/linux-headers-2.6.24-19-generic/include/linux/timer.h:5,
                 from /usr/src/linux-headers-2.6.24-19-generic/include/linux/sched.h:87,
                 from /usr/src/linux-headers-2.6.24-19-generic/include/linux/interrupt.h:12,
                 from hpetimer.c:26:
/usr/src/linux-headers-2.6.24-19-generic/include/linux/ktime.h: In function ‘ktime_set’:
/usr/src/linux-headers-2.6.24-19-generic/include/linux/ktime.h:84: warning: comparison is always false due to limited range of data type
make[1]: *** [hpetimer.o] Error 2
make[1]: Leaving directory `/home/dave/Desktop/alsa/alsa-driver-1.0.9/acore'
make: *** [compile] Error 1





Any ideas?

---

### Post by StandardsDT on 2008-09-10
Anyone able to help me out? It's been about 5 days.

---

