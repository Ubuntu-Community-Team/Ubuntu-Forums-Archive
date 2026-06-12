---
title: "Notebook, Core Duo Compatability"
date: 2007-02-03
forum: Hardware &amp; Laptops
---

### Post by xianthax on 2007-02-03
Anyone had issue with edgy correctly IDing a core Duo proc?  Currently Edgy is only seeing one core ( top only shows CPU0).  I've tried a couple different kernal versions with no success.

anyone else had this problem?

notebook is an Asus A6JC, proc Intel Core Duo....NV 7300 go

Thanks!

-xian

---

### Post by xianthax on 2007-02-03
if it helps.....

/proc/cpuinfo

processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 14
model name      : Genuine Intel(R) CPU           T2300  @ 1.66GHz
stepping        : 8
cpu MHz         : 996.000
cache size      : 2048 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov 
pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc up pni monit
or vmx est tm2 xtpr
bogomips        : 3338.27

---

### Post by quirt3 on 2007-02-03
That's........odd. I'm running a centrino duo with NO issues, generic kernel.

---

### Post by louistan3 on 2007-02-03
which kernel are you using?

i thnk u could check by ```
uname -a
```

you should be using a generic kernel which supports multiple cored processors..

i have an intel core duo and both cores run..

hope this helps.. :D

---

### Post by xianthax on 2007-02-03
>uname -a

Linux xianthax-laptop 2.6.17-10-386 #2 Tue Dec 5 22:26:18 UTC 2006 i686 GNU/Linux


i'm tried the smp package as well with no success.

-xian

---

### Post by Ivan Wagner on 2007-02-18
I'm having the same issue! Did anyone of you solved this problem??

---

### Post by Turmoyl on 2007-02-18
As was already mentioned, the "generic" kernel, which you are not using, has SMP support.  For example, my kernel is 2.6.17-11-generic and it picks up 2 cores without issue.

---

### Post by veloce on 2007-02-18
Assuming you are using the correct (generic) kernel as stated above, also check that your bios hasn't turned off dual core operation.

---

### Post by falcons7 on 2007-03-04
I was looking into this because i also have a dual core t2500 2.0 intel. Turmoyl was correct the smp support is with the generic kernel. Make sure you are booting from the generic one. Also stated was the bios. Many bios' have an option to turn off multiple cores. Hope this helps

---

