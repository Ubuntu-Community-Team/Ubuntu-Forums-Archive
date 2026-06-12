---
title: "can someone help me choose a kernel"
date: 2010-05-31
forum: Hardware
---

### Post by termin on 2010-05-31
hi, i did the cammand:
cat /proc/cpuinfo
and i got this:

processor	: 0
vendor_id	: GenuineIntel
cpu family	: 15
model		: 3
model name	: Intel(R) Pentium(R) 4 CPU 3.00GHz
stepping	: 3
cpu MHz		: 2993.116
cache size	: 1024 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 1
apicid		: 0
initial apicid	: 0
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 5
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe constant_tsc pebs bts pni dtes64 monitor ds_cpl cid
bogomips	: 5986.23
clflush size	: 64
cache_alignment	: 128
address sizes	: 36 bits physical, 32 bits virtual
power management:

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 15
model		: 3
model name	: Intel(R) Pentium(R) 4 CPU 3.00GHz
stepping	: 3
cpu MHz		: 2993.116
cache size	: 1024 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 1
apicid		: 1
initial apicid	: 1
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 5
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe constant_tsc pebs bts pni dtes64 monitor ds_cpl cid
bogomips	: 5985.36
clflush size	: 64
cache_alignment	: 128
address sizes	: 36 bits physical, 32 bits virtual
power management:


what kernel is best for my prosseser (sorry for my spelling)
thanks!

---

### Post by termin on 2010-05-31
anyone please? 
i need ubuntu to run smoothly

---

### Post by termin on 2010-05-31
sorry if am being impationt, but i am just a begenner, so please tell me in baby steps what kernal is best for me
thanks!

---

### Post by termin on 2010-05-31
common, i just need to know please
usually i get replys instantly

---

### Post by oldfred on 2010-05-31
I think it had to be Pentium D to be 64 bit.

If this is yours then it is 32 bit.
[http://ark.intel.com/Product.aspx?id=27508](http://ark.intel.com/Product.aspx?id=27508)

---

### Post by sdennie on 2010-05-31
1) Please don't bump your threads so frequently.

2) Unless you have 4GB+ of RAM, any Ubuntu kernel that boots is just fine.  If you know that you have specialized needs then, yes, a different kernel *might* be an improvement.  However, it's not possible to deduce a "best" kernel based on the output of /proc/cpuinfo.

---

