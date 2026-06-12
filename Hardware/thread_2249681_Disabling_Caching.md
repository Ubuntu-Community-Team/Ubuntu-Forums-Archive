---
title: "Disabling Caching"
date: 2014-10-23
forum: Hardware
---

### Post by James_Orr on 2014-10-23
I'm running experiments where I need to measure the number of CPU cycles  it takes for a L1 and L2 Cache miss (this older computer does not have  an L3 cache). As part of doing this I am wanting to disable the L2 cache  only. I've found kernel modules that will disable all levels of data  caching, but is there a way to only disable a certain level? If so, how?  Any feedback appreciated.

---

### Post by tgalati4 on 2014-10-24
To find if there are any switches for a module:

```
modinfo modulename
```

What is the processor that you are doing your testing?

```
cat /proc/cpuinfo
```

Sometimes BIOS has switches to disable caching, but that is rare.

There may be a system control that allows you to disable the cache while running:

```
man sysctl
```

---

### Post by James_Orr on 2014-10-24
I'm obviously new here. For future reference do I insert one of those code boxes?

The module I've found doesn't have any switches for what I'm wanting to do.

Here are the contents of "cat /proc/cpuinfo":
~$ cat /proc/cpuinfo 
processor    : 0
vendor_id    : GenuineIntel
cpu family    : 15
model        : 3
model name    : Intel(R) Pentium(R) 4 CPU 3.20GHz
stepping    : 4
microcode    : 0xc
cpu MHz        : 3192.306
cache size    : 1024 KB
physical id    : 0
siblings    : 2
core id        : 0
cpu cores    : 1
apicid        : 0
initial apicid    : 0
fdiv_bug    : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 5
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe constant_tsc pebs bts pni dtes64 monitor ds_cpl cid xtpr
bogomips    : 6384.61
clflush size    : 64
cache_alignment    : 128
address sizes    : 36 bits physical, 32 bits virtual
power management:

processor    : 1
vendor_id    : GenuineIntel
cpu family    : 15
model        : 3
model name    : Intel(R) Pentium(R) 4 CPU 3.20GHz
stepping    : 4
microcode    : 0xc
cpu MHz        : 3192.306
cache size    : 1024 KB
physical id    : 0
siblings    : 2
core id        : 0
cpu cores    : 1
apicid        : 1
initial apicid    : 1
fdiv_bug    : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 5
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe constant_tsc pebs bts pni dtes64 monitor ds_cpl cid xtpr
bogomips    : 6384.61
clflush size    : 64
cache_alignment    : 128
address sizes    : 36 bits physical, 32 bits virtual
power management:

---

### Post by tgalati4 on 2014-10-24
Set bit 30 in CR0 to 0 and that will disable caching.

[http://www.osronline.com/article.cfm?article=273](http://www.osronline.com/article.cfm?article=273)

---

### Post by James_Orr on 2014-10-24
That will disable all caching, certainly. I already have a kernel module that will do this. I don't want to know about this, however. My question is whether it is possible to only disable the L2 cache.

---

### Post by tgalati4 on 2014-10-24
I don't think so.  Cache for dual core processors tends to be two-way, set associative, so either core can pull from the cache to process instructions.  So it makes sense to turn it off completely.  But turning off one layer (L2), breaks cache completely.  Why is this an important issue to test?  You would not run any processor without cache.

In older processors, the cache was a separate, supporting chipset (I think Pentium II cards) which you could turn off L1 and L2 separately.  With on-die cache, you can only address the registers that Intel publishes.  Perhaps you can fake an L2 shutdown with some clever coding, but then I wouldn't trust the results and it doesn't represent real workloads.

On really, really old computers, cache was a slot that you could populate with 2, 4, 8 MB RAM.  It was a proprietary slot design and the cache RAM was expensive.

---

### Post by James_Orr on 2014-10-24
I'm developing a model for cache behavior and getting an accurate, machine specific CPU cycle count for a L1 cache hit, L1 cache miss, and L2 cache miss are important for accuracy reasons. The old hardware I'm using does not have an L3 cache. It simply has a shared L2 cache, so I do not think disabling it would completely break everything.

---

### Post by tgalati4 on 2014-10-25
Send an email to Intel and ask them.  They designed the chip, they would know how to turn it off.  How do you handle multi-processor?  Wouldn't you want a single-core processor so that you have a linear data path?

---

