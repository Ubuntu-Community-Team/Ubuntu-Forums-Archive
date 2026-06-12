---
title: "gcc doesn't generate sse2 instructions ?"
date: 2009-05-23
forum: Hardware
---

### Post by Catweazle2009 on 2009-05-23
I can't get gcc to generate sse2 instructions. To verify, I compiled my little test program with the -S option. I explicitly ask gcc to target the pentium-m architecture and generate sse2 instructions:

<start test prog>
#include <stdio.h>
int main(int argc, char** argv)
{
	float f = atof(argv[1]);
	printf("%f\n", f * (float)2.0);
	return 0;
}
<end test prog>

I compile this with gcc -S -march=pentium-m -msse2, and I get:
<start generated assembler>
...
        flds    -8(%ebp)
        fadd    %st(0), %st
        fstpl   4(%esp)
...
<end generated assembler>

This looks like standard i386 fpu math to me, not sse2 !! I've tried all sorts of switches, including -O or -O3, but the generated assembler is always identical.

Anyone ????

Ubuntu 9.04 32-bit running on a Pentium-M Dell Inspiron 1300
catweazle@catweazle-laptop:~/catweazle$ gcc -v
Using built-in specs.
Target: i486-linux-gnu
Configured with: ../src/configure -v --with-pkgversion='Ubuntu 4.3.3-5ubuntu4' --with-bugurl=file:///usr/share/doc/gcc-4.3/README.Bugs --enable-languages=c,c++,fortran,objc,obj-c++ --prefix=/usr --enable-shared --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --with-gxx-include-dir=/usr/include/c++/4.3 --program-suffix=-4.3 --enable-clocale=gnu --enable-libstdcxx-debug --enable-objc-gc --enable-mpfr --enable-targets=all --with-tune=generic --enable-checking=release --build=i486-linux-gnu --host=i486-linux-gnu --target=i486-linux-gnu
Thread model: posix
gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4)

catweazle@catweazle-laptop:~/catweazle$ cat /proc/cpuinfo
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 13
model name	: Intel(R) Celeron(R) M processor         1.60GHz
stepping	: 8
cpu MHz		: 1596.043
cache size	: 1024 KB
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 2
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss tm pbe nx up bts
bogomips	: 3192.08
clflush size	: 64
power management:

---

### Post by rjdriscoll on 2009-05-24
You need to use "-mfpmath=sse" as well.

For example on my AMD Athlon X2 I've been using:

 "-march=native -mfpmath=sse"

The library will still be fp87 though unless you rebuild it and so will the function calling conventions unless you put:-

  "__attribute__ ((sseregparm))"

.. after each function definition.

Hope this helps.

Richard

---

