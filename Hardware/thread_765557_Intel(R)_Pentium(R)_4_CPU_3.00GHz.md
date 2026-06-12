---
title: "Intel(R) Pentium(R) 4 CPU 3.00GHz"
date: 2008-04-24
forum: Hardware
---

### Post by quest23 on 2008-04-24
first off..sorry if this is a dumb question ..i really tried to find these answers but had no luck searching..

i have a question about the processor in the title.  

my computer is a hp pavillion a450n

i was wondering if first is this a dual core processor? 
when i look in system info it shows two processors.

also..is this processor compatable to use ubuntu 64 bit..or do i have to use the x86 version 32bit.  i heard that the 64 bit version runs a little better thats the only reason i ask..i currently have gutsy x86..but wanted to use the new edition 64 bit but didnt know if i could..here is my computer info from terminal..it too shows two processors...

 cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 15
model           : 3
model name      : Intel(R) Pentium(R) 4 CPU 3.00GHz
stepping        : 3
cpu MHz         : 3000.160
cache size      : 1024 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 1
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 5
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe constant_tsc pni monitor ds_cpl cid
bogomips        : 6005.12
clflush size    : 64

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 15
model           : 3
model name      : Intel(R) Pentium(R) 4 CPU 3.00GHz
stepping        : 3
cpu MHz         : 3000.160
cache size      : 1024 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 1
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 5
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe constant_tsc pni monitor ds_cpl cid
bogomips        : 6000.68
clflush size    : 64

---

### Post by stinger30au on 2008-04-24
is this cpu a dual core cpu???? well to the software it is as it has hypertreading turned on.

but the physical internals of the cpu is a single core cpu.

hyperthreading has been made pretty much obsolete by dual core cpus.


hope this helps

---

### Post by stinger30au on 2008-04-24
it is a 32 bit cpu

---

### Post by hembergler on 2008-04-24
You have a 32-bit CPU with Hyperthreading (which the OS interprets as dual-core)

---

### Post by quest23 on 2008-04-24
so does that mean that i can use the 64 bit os...or do i have to stick with 32 bit...

---

### Post by fhantazm on 2008-04-25
You have to stick with 32bit Ubuntu. Which I actually prefer.

---

### Post by MaxTrax on 2012-10-03
I have been searching online to verify the bit type of mine as well, and am getting confused. Most places say that Pentium 4 is all 32-bit...minus the last one or two versions. On a linux forum, they said that if "lm" is the Flags section, it is 64-bit. Is this true?
> processor    : 0
vendor_id    : GenuineIntel
cpu family    : 15
model        : 4
model name    : Intel(R) Pentium(R) 4 CPU 3.00GHz
stepping    : 3
microcode    : 0x5
cpu MHz        : 1400.000
cache size    : 2048 KB
physical id    : 0
siblings    : 2
core id        : 0
cpu cores    : 1
apicid        : 0
initial apicid    : 0
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 5
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc pebs bts pni dtes64 monitor ds_cpl est cid cx16 xtpr
bogomips    : 5984.76
clflush size    : 64
cache_alignment    : 128
address sizes    : 36 bits physical, 48 bits virtual
power management:

---

### Post by drmrgd on 2012-10-03
This thread is likely to get closed as it's very old, and bumping such old threads is discouraged here.  So, you may be better off starting a new post.

That being said, it is true that the 'lm' flag is an indicator of 64-bit architecture.  You can also run the following to see the supported operating modes:

```
lscpu
```

Hope that helps.  If this gets locked and you still need more help, feel free to start a new thread on this topic.

---

### Post by MaxTrax on 2012-10-03
It did help, thank you. I am a novice at non-Windows OS, so Google has become my friend/enemy here.

---

