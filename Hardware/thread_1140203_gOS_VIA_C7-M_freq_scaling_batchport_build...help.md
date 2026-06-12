---
title: "gOS VIA C7-M freq scaling batchport build...help"
date: 2009-04-27
forum: Hardware
---

### Post by intrepid7 on 2009-04-27
I updated my sylvania gnetbook to gOS 3.0 , everything is pretty smooth but I have been trying to fix the freq scaling issue. 

mpdion@gnetbook:~$ cat /proc/cpuinfo
processor	: 0
vendor_id	: CentaurHauls
cpu family	: 6
model		: 13
model name	: VIA C7-M Processor 1200MHz
stepping	: 0
cpu MHz		: 600.046
cache size	: 128 KB
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 1
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge cmov pat clflush acpi mmx fxsr sse sse2 tm nx pni est tm2 xtpr rng rng_en ace ace_en ace2 ace2_en phe phe_en pmm pmm_en
bogomips	: 1200.63
clflush size	: 64


So, the est flag means this processor does support frequency scaling but the old kernel installed does not.  So, I follow the directions here:[http://www.a110wiki.de/wiki/CPU](http://www.a110wiki.de/wiki/CPU)

$ wget [http://www.a110wiki.de/wiki/images/6...ckport.tar.bz2](http://www.a110wiki.de/wiki/images/6...ckport.tar.bz2)
$ tar xfvj Cpufreq-2.6.25_backport.tar.bz2
$ cd cpufreq
$ make

However, when I try to make the module I get a slew of returned errors, ie:
mpdion@gnetbook:~/cpufreq$ make
make -C /lib/modules/`uname -r`/build M=`pwd` modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24.3'
/usr/src/linux-headers-2.6.24.3/arch/x86/Makefile:15: /usr/src/linux-headers-2.6.24.3/arch/x86/Makefile_32: No such file or directory
CC [M] /home/mpdion/cpufreq/e_powersaver.o
In file included from include/linux/kernel.h:11,
from /home/mpdion/cpufreq/e_powersaver.c:9:
include/linux/linkage.h:4:25: error: asm/linkage.h: No such file or directory
In file included from include/linux/posix_types.h:47,
from include/linux/types.h:11,
from include/linux/kernel.h:13,
.
.
.
and so on. I have installed the build-essentials package. Has anyone had this problem, any fixes? Thanks

---

