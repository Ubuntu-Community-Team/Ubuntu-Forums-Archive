---
title: "need my 32 bit to recognize more ram"
date: 2011-10-04
forum: Hardware
---

### Post by murderd2death on 2011-10-04
I'm running 11.04 right now, and i've reinstalled natty a few times this past month on this same system, and i've noticed that every time it recognizes a different amount of ram. Anywhere from 2.5 or 2.1 or as of this installation only 1.9 gigs of ram out of the 4 gigs i actually have. The laptop is a lenovo b570 and i want to find a way to get it to recognize ALL of my ram. can you guys help? 

regards

---

### Post by Kilz on 2011-10-04
I looked up the specifications for your laptop, it has a 64bit processor. Simple solution, install the 64bit version of ubuntu that will see all your ram and make full use of the hardware (64bit cpu) you paid good money for. Test it out with the live version of the install cd/usb.

---

### Post by kurt18947 on 2011-10-04
> **Kilz said:**
> I looked up the specifications for your laptop, it has a 64bit processor. Simple solution, install the 64bit version of ubuntu that will see all your ram and make full use of the hardware (64bit cpu) you paid good money for. Test it out with the live version of the install cd/usb.

Kilz has the best idea. The other option would be to open Synaptic (install from the Software Center if you don't) and do a search for "pae".  You should find your kernel version with pae extensions.  I'm surprised the pae kernel didn't install by default, mine does.  Pae is not the preferred choice but it should work.  Here's what my choices would be if I weren't running 64 bit.
[ATTACH]203537[/ATTACH]

I don't know if you'd have to run "update-grub" for the new kernels to be recongized or not because I've never had to do install a pae kernel manually.

---

### Post by murderd2death on 2011-10-04
> **Kilz said:**
> I looked up the specifications for your laptop, it has a 64bit processor. Simple solution, install the 64bit version of ubuntu that will see all your ram and make full use of the hardware (64bit cpu) you paid good money for. Test it out with the live version of the install cd/usb.

i've always had problems installing 62 bit linux versions on here, it wont read the live cd from from startup unless its 32 bit.

---

### Post by murderd2death on 2011-10-04
> **kurt18947 said:**
> Kilz has the best idea. The other option would be to open Synaptic (install from the Software Center if you don't) and do a search for "pae".  You should find your kernel version with pae extensions.  I'm surprised the pae kernel didn't install by default, mine does.  Pae is not the preferred choice but it should work.  Here's what my choices would be if I weren't running 64 bit.
[ATTACH]203537[/ATTACH]

I don't know if you'd have to run "update-grub" for the new kernels to be recongized or not because I've never had to do install a pae kernel manually.

linux-generic-pae is installed, not linux-generic-pae:i386.

---

### Post by thatguruguy on 2011-10-04
> **murderd2death said:**
> i've always had problems installing 62 bit  linux versions on here, it wont read the live cd from from startup  unless its 32 bit.

FWIW, it's 64-bit, not 62-bit.  Have you tried it from a USB stick?

> **murderd2death said:**
> linux-generic-pae is installed, not linux-generic-pae:i386.

There are no pae packages for 64-bit, since it's unnecessary.  However, it sounds more like a hardware problem than a software problem, if you are regularly getting different values for your installed ram.  Run the following in a terminal, and post the results in this thread:
```
free -m
```

---

### Post by murderd2death on 2011-10-04
> **thatguruguy said:**
> FWIW, it's 64-bit, not 62-bit.  Have you tried it from a USB stick?

i have tried USB sticks, those don't work well with 64 bit either.



> There are no pae packages for 64-bit, since it's unnecessary.  However, it sounds more like a hardware problem than a software problem, if you are regularly getting different values for your installed ram.  Run the following in a terminal, and post the results in this thread:
```
free -m
``````
             total       used       free     shared    buffers     cached
Mem:          1900       1215        684          0         52        653
-/+ buffers/cache:        509       1390
Swap:         7627          0       7627

```

---

### Post by murderd2death on 2011-10-04
> **Kilz said:**
> I looked up the specifications for your laptop, it has a 64bit processor. Simple solution, install the 64bit version of ubuntu that will see all your ram and make full use of the hardware (64bit cpu) you paid good money for. Test it out with the live version of the install cd/usb.

im burning another 64 bit live cd right now, just for reference before i get started trying again; if i get through and then have the option to install 64 bit, can i do the 'upgrade 11.04 to 11.04' option that will save all my settings and files and such? or is the fact that its different architecture render that not an option.

---

### Post by Kilz on 2011-10-04
please open a terminal and type

cat /proc/cpuinfo

Hit enter and paste the results to a post here.

---

### Post by murderd2death on 2011-10-04
> **Kilz said:**
> please open a terminal and type

cat /proc/cpuinfo

Hit enter and paste the results to a post here.
```
processor    : 0
vendor_id    : GenuineIntel
cpu family    : 6
model        : 42
model name    : Intel(R) Pentium(R) CPU B940 @ 2.00GHz
stepping    : 7
cpu MHz        : 2000.000
cache size    : 2048 KB
physical id    : 0
siblings    : 2
core id        : 0
cpu cores    : 2
apicid        : 0
initial apicid    : 0
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 13
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx rdtscp lm constant_tsc arch_perfmon pebs bts xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 x2apic popcnt xsave lahf_lm arat epb xsaveopt pln pts dts
bogomips    : 3990.74
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

processor    : 1
vendor_id    : GenuineIntel
cpu family    : 6
model        : 42
model name    : Intel(R) Pentium(R) CPU B940 @ 2.00GHz
stepping    : 7
cpu MHz        : 800.000
cache size    : 2048 KB
physical id    : 0
siblings    : 2
core id        : 1
cpu cores    : 2
apicid        : 2
initial apicid    : 2
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 13
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx rdtscp lm constant_tsc arch_perfmon pebs bts xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 x2apic popcnt xsave lahf_lm arat epb xsaveopt pln pts dts
bogomips    : 3990.74
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

```

---

### Post by murderd2death on 2011-10-04
so i just ran a freshly burnt 64 bit live cd of natty and i couldn't get passed the 'try installing ubuntu' menu. So until i figure that part out i'd like to get all of my ram recognized.

---

### Post by thatguruguy on 2011-10-04
> **murderd2death said:**
> i have tried USB sticks, those don't work well with 64 bit either.



```
             total       used       free     shared    buffers     cached
Mem:          1900       1215        684          0         52        653
-/+ buffers/cache:        509       1390
Swap:         7627          0       7627

```

This still looks like a hardware issue to me. Check your bios for how much memory your computer is seeing. 

As an aside, why do you have such a large swap file.

---

### Post by murderd2death on 2011-10-04
> **thatguruguy said:**
> 
As an aside, why do you have such a large swap file.

i was planning to have 4 gigs of ram and have the swap doubled off of that.

---

### Post by murderd2death on 2011-10-04
> **thatguruguy said:**
> This still looks like a hardware issue to me. Check your bios for how much memory your computer is seeing. 

k, i checked the bios and it gave me relatively the same reading, so i got grounded and popped open my laptop and found out one of my RAM chips had loosened, thankfully at both ends so it didn't fry. I got it back in properly and am reading 4 gigs of ram. problem solved.

---

### Post by thatguruguy on 2011-10-04
Glad you got it sorted out.

I would hazard a guess that this may have been at the root of your problem w/r/t installing the 64-bit version of Ubuntu, as well.

Incidentally, although there may be some benefit in having your swap file be the same size as your ram (since ubuntu will use it when you put your computer in hibernation mode), you don't really need to have double the size of ram in your swap file.  You're really just wasting disk space.  But that is, of course, up to you.

---

### Post by Kilz on 2011-10-04
Before burning that cd, did you check the md5sum of the image you downloaded? I dont understand why you cant boot the 64bit edition, perhaps you need to file a bug report.[ Because your processor is 64bit according to Intel]("http://ark.intel.com/products/55626/Intel-Pentium-Processor-B940-%282M-Cache-2_00-GHz%29")

Instruction Set               64-bit

You really do want to try the 64bit version, because right now your computer is not giving you the full benefit of the CPU you paid good money for.

---

