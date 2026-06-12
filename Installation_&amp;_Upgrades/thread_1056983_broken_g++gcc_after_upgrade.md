---
title: "broken g++/gcc after upgrade"
date: 2009-02-01
forum: Installation &amp; Upgrades
---

### Post by andrewkay on 2009-02-01
(in intrepid) I clicked the gnome updater tool, as it said there were important security updates, including new kernel (working fine except for invidia drivers of course) and new gcc/g++ 4.3.2.  There were around 90MB in all...

Now gcc (and g++) are broken:  For example, gcc cannot find <stdio.h>

There *is* a stdio.h on the system (is it in the right place?)

Help! Please!

```
$ find /usr -name stdio.h
/usr/include/c++/4.3/tr1/stdio.h
$ uname -a
Linux xyz 2.6.27-11-generic #1 SMP Thu Jan 29 19:24:39 UTC 2009 i686 GNU/Linux
$ gcc --version
gcc (Ubuntu 4.3.2-1ubuntu12) 4.3.2

```

I think there must be some libc header files missing, but I can't guess which package they are supposed to be in.

synaptic lists these files installed for package libc6-dev, version
2.8~20080505-0ubuntu8(intrepid-updates) -- no header files here.

```
/.
/usr
/usr/bin
/usr/bin/gencat
/usr/bin/mtrace
/usr/bin/rpcgen
/usr/bin/sprof
/usr/lib
/usr/lib/libanl.a
/usr/lib/libBrokenLocale.a
/usr/lib/libbsd-compat.a
/usr/lib/libc.a
/usr/lib/libc_nonshared.a
/usr/lib/libcrypt.a
/usr/lib/libdl.a
/usr/lib/libg.a
/usr/lib/libieee.a
/usr/lib/libm.a
/usr/lib/libmcheck.a
/usr/lib/libnsl.a
/usr/lib/libpthread.a
/usr/lib/libpthread_nonshared.a
/usr/lib/libresolv.a
/usr/lib/librpcsvc.a

```


gcc with -v tells me:
```

$ gcc -v -o simple simple.c
Using built-in specs.
Target: i486-linux-gnu
Configured with: ../src/configure -v --with-pkgversion='Ubuntu 4.3.2-1ubuntu12' --with-bugurl=file:///usr/share/doc/gcc-4.3/README.Bugs --enable-languages=c,c++,fortran,objc,obj-c++ --prefix=/usr --enable-shared --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --with-gxx-include-dir=/usr/include/c++/4.3 --program-suffix=-4.3 --enable-clocale=gnu --enable-libstdcxx-debug --enable-objc-gc --enable-mpfr --enable-targets=all --enable-checking=release --build=i486-linux-gnu --host=i486-linux-gnu --target=i486-linux-gnu
Thread model: posix
gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu12) 
COLLECT_GCC_OPTIONS='-v' '-o' 'simple' '-mtune=generic'
 /usr/lib/gcc/i486-linux-gnu/4.3.2/cc1 -quiet -v simple.c -D_FORTIFY_SOURCE=2 -quiet -dumpbase simple.c -mtune=generic -auxbase simple -version -fstack-protector -o /tmp/cczIrMJD.s
ignoring nonexistent directory "/usr/local/include/i486-linux-gnu"
ignoring nonexistent directory "/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../i486-linux-gnu/include"
#include "..." search starts here:
#include <...> search starts here:
 /usr/local/include
 /usr/lib/gcc/i486-linux-gnu/4.3.2/include
 /usr/lib/gcc/i486-linux-gnu/4.3.2/include-fixed
 /usr/include/i486-linux-gnu
 /usr/include
End of search list.
GNU C (Ubuntu 4.3.2-1ubuntu12) version 4.3.2 (i486-linux-gnu)
	compiled by GNU C version 4.3.2, GMP version 4.2.2, MPFR version 2.3.2.
GGC heuristics: --param ggc-min-expand=100 --param ggc-min-heapsize=131072
Compiler executable checksum: 9ecd6562c106044a1f3a6d56a4b5859b
simple.c:1:19: error: stdio.h: No such file or directory
simple.c: In function &#8216;main&#8217;:
simple.c:5: warning: incompatible implicit declaration of built-in function &#8216;printf&#8217;

```

Finally, here's the input file "simple.c":
```

#include <stdio.h>
int main (int argc, char **argv) 
{ 
	printf ("hello world.\n"); 
	return 0; 
}

```

---

### Post by andrewkay on 2009-02-01
Fixed -- looks like the package file was corrupted.  Why can't this be detected automatically?  Fixed by forcing synaptic to download the package again.

```

$ cd /var/cache/apt/archives
$ od -a libc6-dev_2.8~20080505-0ubuntu8_i386.deb.BROKEN > ~/tmp/brok
$ od -a libc6-dev_2.8~20080505-0ubuntu8_i386.deb > ~/tmp/ok
$ cd ~/tmp
$ diff ok brok | more
85717c85717
< 5166500 etb   u dc2   *   7   4  so   3   I   I  sp   3   ?  ff   t   f 
---
> 5166500 etb   5 dc2   *   7   4  so   3   I   I  sp   3   ?  ff   t   f
185941c185941
< 13262500 del   G   ~ del   5   x del   K   v   `   J   n   q nak   . nul
---
> 13262500 del bel   ~ del   5   x del   K   v   `   J   n   q nak   . nul

```

---

### Post by neo unplugged on 2011-03-09
@andrewkay:
I have a similar issue. How did u force synaptic to reinstall the package? Could you post a link on how to do it or the command?
Thank you.

---

### Post by IcarusR on 2011-03-09
Use apt-get from the terminal. Check the man page for details, in a terminal

```
man apt-get
```

As this thread is over a year old you would do better to start your own thread.

---

