---
title: "[SOLVED] Compiling Performance Counter Library (PCL) in Intrepid"
date: 2008-11-14
forum: General Help
---

### Post by fowie on 2008-11-14
Has anyone tried to compile the PCL ([http://www.fz-juelich.de/jsc/PCL/](http://www.fz-juelich.de/jsc/PCL/)) in Intrepid?  I've patched my kernel but the Makefile is having issues finding linux/smp.h  Anyone up for some in-depth debugging?

Here's the output of ./make:
```

(cd src; make default)
make[1]: Entering directory `/home/fowie/PCL/pcl_2.2/src'
(cd /home/fowie/PCL/pcl_2.2/src/machines/PENTIUM_LINUX; make)
make[2]: Entering directory `/home/fowie/PCL/pcl_2.2/src/machines/PENTIUM_LINUX'
gcc -c -g -O2 -DLINUX -I/home/fowie/PCL/pcl_2.2/src -I/home/fowie/PCL/pcl_2.2/src/machines/PENTIUM_LINUX  -O3 -fomit-frame-pointer -funroll-loops -Wall -I/usr/lib/jvm/java-6-sun/include -I/usr/lib/jvm/java-6-sun/include/linux -I./perfctr/usr.lib -o /home/fowie/PCL/pcl_2.2/bin/i686-pc-linux-gnu/determine_mhz.o determine_mhz.c
determine_mhz.c: In function &#8216;PCL_determine_mhz_rate&#8217;:
determine_mhz.c:137: warning: dereferencing type-punned pointer will break strict-aliasing rules
determine_mhz.c:148: warning: dereferencing type-punned pointer will break strict-aliasing rules
gcc -c -g -O2 -DLINUX -I/home/fowie/PCL/pcl_2.2/src -I/home/fowie/PCL/pcl_2.2/src/machines/PENTIUM_LINUX  -O3 -fomit-frame-pointer -funroll-loops -Wall -I/usr/lib/jvm/java-6-sun/include -I/usr/lib/jvm/java-6-sun/include/linux -I./perfctr/usr.lib -o /home/fowie/PCL/pcl_2.2/bin/i686-pc-linux-gnu/processor_number.o processor_number.c
processor_number.c:69:23: error: linux/smp.h: No such file or directory
processor_number.c: In function &#8216;PCL_processor_number&#8217;:
processor_number.c:79: warning: implicit declaration of function &#8216;smp_processor_id&#8217;
make[2]: *** [/home/fowie/PCL/pcl_2.2/bin/i686-pc-linux-gnu/processor_number.o] Error 1
make[2]: Leaving directory `/home/fowie/PCL/pcl_2.2/src/machines/PENTIUM_LINUX'
make[1]: *** [machine_all] Error 2
make[1]: Leaving directory `/home/fowie/PCL/pcl_2.2/src'
make: *** [all] Error 2

```

---

### Post by fowie on 2008-12-09
This is probably not a hot topic here, but someday someone will come looking for an answer about this and they'll see this--be sure to hit the little "thank you" icon, Mr. or Ms. 30-years-from-now...

PCL is no longer in use, so don't try to use it.  Use PAPI instead: [http://www.cs.drexel.edu/~tc365/papi.html](http://www.cs.drexel.edu/~tc365/papi.html)
and
[http://www.google.com/url?sa=t&source=web&ct=res&cd=1&url=http%3A%2F%2Ficl.cs.utk.edu%2Fpapi%2F&ei=nK4-SbuaGomGsQP0kOW0Cg&usg=AFQjCNH0cBrBMfo-FbKETZ5LaMm4nD-0og&sig2=wLo34FeTZFZOm_9k0ahqhg](http://www.google.com/url?sa=t&source=web&ct=res&cd=1&url=http%3A%2F%2Ficl.cs.utk.edu%2Fpapi%2F&ei=nK4-SbuaGomGsQP0kOW0Cg&usg=AFQjCNH0cBrBMfo-FbKETZ5LaMm4nD-0og&sig2=wLo34FeTZFZOm_9k0ahqhg)

---

