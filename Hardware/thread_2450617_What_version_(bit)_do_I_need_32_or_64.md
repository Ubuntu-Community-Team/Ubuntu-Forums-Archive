---
title: "What version (bit) do I need? 32 or 64?"
date: 2020-09-17
forum: Hardware
---

### Post by sofasurfer on 2020-09-17
uname -m shows that I have a i686 processor. uname -a shows Linux daryl-Inspiron-660 4.4.0-189-generic #219-Ubuntu SMP Tue Aug 11 12:22:40 UTC 2020 i686 i686 i686 GNU/Linux. cat /proc/cpuinfo | grep "model name" shows model name	: Intel(R) Core(TM) i3-2100 CPU @ 3.10GHz.

Doesn't all of this mean that I have an old slow processor with 32 bit?

I currently run Ubuntu 16.04. I have used it for 4 years. It has been great but with this current pc I have had a lot of trouble with black screen and freezeups. I assume this is because of my processor.
I am considering using a different version of linux but I need to know if I need to use 32 bit or 64 bit.
Also, I want to try a different distro than ubuntu. What distro do you recommend for ordinary daily internet use where I can install packages from other distros using synaptic or package manager?

---

### Post by CatKiller on 2020-09-17
[https://ark.intel.com/content/www/us/en/ark/products/53422/intel-core-i3-2100-processor-3m-cache-3-10-ghz.html](https://ark.intel.com/content/www/us/en/ark/products/53422/intel-core-i3-2100-processor-3m-cache-3-10-ghz.html)

> Instruction Set 64-bit

---

### Post by deadflowr on 2020-09-17
You're running a 32-bit kernel on a i3 machine which should be 64-bit capable.

> I am considering using a different version of linux but I need to know if I need to use 32 bit or 64 bit.
Going forward, much like Ubuntu linux systems are slowly dropping 32-bit, so you'll have to run 64-bit eventually.
At least if you want smooth daily usage without a ton of hassle to get going.

> What distro do you recommend for ordinary daily internet use where I can install packages from other distros using synaptic or package manager?
Probably depends on which distro or distro-type you are looking to try.
But all have at least a command line package management system, like apt.

>  It has been great but with this current pc I have had a lot of trouble with black screen and freezeups. I assume this is because of my processor.
I doubt it's because of the cpu model, but maybe is faulty like bad ram or failing hard drive, or possible cpu failing. or even bad gpu or the gpu drivers.
Could be a number of reasons, but I wouldn't think it's the cpu model at fault.

---

### Post by CelticWarrior on 2020-09-17
[https://ark.intel.com/content/www/br/pt/ark/products/53422/intel-core-i3-2100-processor-3m-cache-3-10-ghz.html](https://ark.intel.com/content/www/br/pt/ark/products/53422/intel-core-i3-2100-processor-3m-cache-3-10-ghz.html)

Your CPU is 64-bit.
So, you installed Ubuntu 16.04 32-bit because you wanted to, not because you needed to.
Try Ubuntu 20.04 (64-bit only) in a live session to see if it has the same problems of "[COLOR=#000000]black screen and freezeups".[/COLOR]
[COLOR=#000000]Also, do you have a discrete graphics cards? If you don't maybe you should because depending only on an old Intel iGPU that is no longer supported (for several years now) can't possibly give you a good experience. The cheapest second-hand Nvidia or AMD you can find at eBay will be an huge performance boost.[/COLOR]
[COLOR=#000000]And finally, old hardware struggles, often a lot, with standard Ubuntu with Gnome. Prefer lighter variants like Xubuntu and Lubuntu. Even the current Kubuntu (KDE) will give better results than the standard Ubuntu.[/COLOR]

---

### Post by sofasurfer on 2020-09-17
Thanks for your answers. But keep them coming. I am learning a lot. 
I don't understand how I have a 32 bit cpu (according to the commands that I posted) and still say I have a 64 bit cpu.

---

### Post by deadflowr on 2020-09-17
> I don't understand how I have a 32 bit cpu (according to the commands that I posted) 
The command only outputs the arch for the running kernel, not the actual cpu architecture.

To add,
You can look at
```
lscpu
```
for better output of the processor and it's capabilities.
Should have a line for* CPU op-modes* which should tell what arch are available to run.

---

### Post by guiverc on 2020-09-17
> **sofasurfer said:**
> Thanks for your answers. But keep them coming. I am learning a lot. 
I don't understand how I have a 32 bit cpu (according to the commands that I posted) and still say I have a 64 bit cpu.

@deadflowr has already describee why your system is likely i686 (that was what you installed).

I'll suggest you may have installed the 32-bit version as that was the windows version on your machine before you switched to Ubuntu; thus you knew it would work.

Microsoft charged $5 extra for 64-bit windows, so most consumer grade computers sold with 32-bit versions of windows even though the hardware was 64-bit. Buyers understood the $5 far more than the 32 vs 64 bit operating system option (it also suited the OEMs too, who used it help up-sell better laptops should the consumer need 64-bit windows).

Ubuntu *flavors* can be found at [https://ubuntu.com/download/flavours](https://ubuntu.com/download/flavours) , though the choice of which *flavor* best suits you, really only you can decide. Sort of like which ice-cream is best (ps: it's chocolate!)

---

### Post by mastablasta on 2020-09-18
32 bit used to also be recommended for quite some time.
you can install 64 bit OS because the CPu is 64 bit.
however, just installing 64 bit will likely not help with freezing and black screens.

---

### Post by scorp123 on 2020-09-18
> **sofasurfer said:**
>  cat /proc/cpuinfo | grep "model name" 

You're grep'ping for the wrong thing. ;)   What you want to look out for is not the "model name" but the CPU flags your CPU reports back:

```

 cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 79
model name      : Intel(R) Xeon(R) CPU E5-2650 v4 @ 2.20GHz
stepping        : 1
microcode       : 0xb000036
cpu MHz         : 2194.917
cache size      : 30720 KB
physical id     : 0
siblings        : 1
core id         : 0
cpu cores       : 1
apicid          : 0
initial apicid  : 0
fpu             : yes
fpu_exception   : yes
cpuid level     : 20
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts mmx fxsr sse sse2 ss syscall nx pdpe1gb rdtscp **[COLOR="#FF0000"]lm[/COLOR]**
 constant_tsc arch_perfmon pebs bts nopl xtopology tsc_reliable nonstop_tsc aperfmperf eagerfpu pni pclmulqdq ssse3 fma cx16 pcid sse4_1
 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand hypervisor lahf_lm abm 3dnowprefetch epb invpcid_single
 fsgsbase tsc_adjust bmi1 hle avx2 smep bmi2 invpcid rtm rdseed adx smap xsaveopt dtherm ida arat pln pts
bogomips        : 4389.83
clflush size    : 64
cache_alignment : 64
address sizes   : 42 bits physical, 48 bits virtual
power management:

```

The flag you want to look out for is "lm" which stands for "Long Mode" and means "64-bit".  Old 32-bit CPU's don't have that and thus this flag won't show there.

---

### Post by mikewhatever on 2020-09-18
So, <uname -a> is obviously not the way to check CPU architecture. Try <lscpu> instead.

```

~$ lscpu
Architecture:                    x86_64
CPU op-mode(s):                  32-bit, 64-bit
Byte Order:                      Little Endian
...

```

---

