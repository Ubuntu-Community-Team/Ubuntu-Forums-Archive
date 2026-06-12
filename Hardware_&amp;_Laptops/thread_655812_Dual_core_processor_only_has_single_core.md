---
title: "Dual core processor only has single core"
date: 2008-01-01
forum: Hardware &amp; Laptops
---

### Post by intense.ego on 2008-01-01
My processor is an Intel Core Duo T2400 1.83 ghz. I looked up my processor on wikipedia and it says it is dual core ([http://en.wikipedia.org/wiki/List_of...ors#Intel_Core](http://en.wikipedia.org/wiki/List_of...ors#Intel_Core)). Also, my laptop has this ([http://en.wikipedia.org/wiki/Image:C...LogoV3-Duo.png](http://en.wikipedia.org/wiki/Image:C...LogoV3-Duo.png)) sticker on it. However, while trying to configure conky (a system monitor) i kept on getting messages saying i was trying to use more CPUs than i had (i.e. i had a single core processor as opposed to dual core). Could it be possible that Ubuntu does not recognize my second core? My only other guess is that either it is an Intel Core Solo ([http://en.wikipedia.org/wiki/Intel_Core#Yonah](http://en.wikipedia.org/wiki/Intel_Core#Yonah)) that only ever had one active core or that one core became defective since being made. Can anyone shed any light onto my situation?

My output for 
```
cat /proc/cpuinfo
```
was
```
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 14
model name      : Genuine Intel(R) CPU           T2400  @ 1.83GHz
stepping        : 8
cpu MHz         : 1833.000
cache size      : 2048 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss tm pbe nx constant_tsc up pni monitor vmx est tm2 xtpr
bogomips        : 3661.57
clflush size    : 64
```

Because I am dual-booting I could boot into windows and see what comes up but I have not used it since installing Ubuntu (and I have repartitioned my hard drive several times since) and would prefer if there was another way.

---

### Post by overdrank on 2008-01-01
Ok you can use the command ```
lshw | less
``` To verify if it is not recognized. 
Example
```
          product: AMD Athlon(tm) 64 X2 Dual Core Processor 4200+
          vendor: Advanced Micro Devices [AMD]
          physical id: 1
          bus info: cpu@0
          version: 15.11.2
          size: 1GHz
          capacity: 1GHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic
 sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext 
fxsr_opt x86-64 3dnowext 3dnow pni cx16 lahf_lm cmp_legacy svm cr8legacy ts fid 
vid ttp tm stc cpufreq
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 128KB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 512KB
```

---

### Post by intense.ego on 2008-01-01
I tried the command you gave me, overdrank, and this is what I got:
```
product: Genuine Intel(R) CPU           T2400  @ 1.83GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.14.8
          serial: 0000-06E8-0000-0000-0000-0000
          size: 1GHz
          capacity: 1GHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic
 sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss tm pbe nx const
ant_tsc up pni monitor vmx est tm2 xtpr cpufreq

```

---

### Post by jespdj on 2008-01-02
The [T2400](http://processorfinder.intel.com/details.aspx?sspec=sl9jm) is a Core Duo processor. It is a dual-core processor, so Ubuntu should see two cores.

First, have a look at the BIOS settings, and see if both cores are enabled there. If that isn't it, you could try a BIOS update. Go to the website of the manufacturer of your laptop and see if there's a BIOS update available for your laptop model.

---

### Post by intense.ego on 2008-01-02
I just checked on the Lenovo website (my laptop is a Thinkpad T60), but there does not seem to be any BIOS updates, only firmware updates for the drive. Link: [http://www-307.ibm.com/pc/support/site.wss/product.do?template=/product.do?template=%2Fproductpage%2Flandingpages%2FproductPageLandingPage.vm&sitestyle=lenovo&brandind=10&familyind=290543&machineind=293746&modelind=293751&partnumberind=0&subcategoryind=0&doctypeind=9&doccategoryind=0&operatingsystemind=52305&validate=true](http://www-307.ibm.com/pc/support/site.wss/product.do?template=/product.do?template=%2Fproductpage%2Flandingpages%2FproductPageLandingPage.vm&sitestyle=lenovo&brandind=10&familyind=290543&machineind=293746&modelind=293751&partnumberind=0&subcategoryind=0&doctypeind=9&doccategoryind=0&operatingsystemind=52305&validate=true)
I am going to reboot into my BIOS as soon as I can and will post my findings.

---

### Post by jeffus_il on 2008-01-02
Would be interesting to see:
dmesg | grep CPU

---

### Post by intense.ego on 2008-01-02
I just ran that command jeffus_il and I got this confusing message:

```
 [98765.548000] Uhhuh. NMI received for unknown reason a1 on CPU 0. 
```

---

### Post by intense.ego on 2008-01-02
UPDATE: I entered my BIOS, went under config and then under CPU. I noticed that there was option titled something like "Multiple Core Processing" and that it was disabled. I enabled it, booted into Ubuntu and now, when i go to sysinfo, it says I have two cores. 

The output of cat /proc/cpuinfo is now the following

```
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 14
model name      : Genuine Intel(R) CPU           T2400  @ 1.83GHz
stepping        : 8
cpu MHz         : 1000.000
cache size      : 2048 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 2
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc pni monitor vmx est tm2 xtpr
bogomips        : 3661.59
clflush size    : 64

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 6
model           : 14
model name      : Genuine Intel(R) CPU           T2400  @ 1.83GHz
stepping        : 8
cpu MHz         : 1000.000
cache size      : 2048 KB
physical id     : 0
siblings        : 2
core id         : 1
cpu cores       : 2
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc pni monitor vmx est tm2 xtpr
bogomips        : 3657.60
clflush size    : 64

```

EDIT:
I have a couple of questions. Firstly (and this is a bit paranoid), is there anything wrong with having used my laptop for 6 months using only one processor (i.e. the one processor that was active would have had to work really hard for those 6 months and the one that was inactive might be "out of shape")? Secondly, my system monitory (conky) says "Core 1: 1000 MHz" and "Core 2: 1000 MHz" but occasionally flash as 1833 MHz. What is up with that?

---

### Post by overdrank on 2008-01-02
> **intense.ego said:**
> UPDATE: I entered my BIOS, went under config and then under CPU. I noticed that there was option titled something like "Multiple Core Processing" and that it was disabled. I enabled it, booted into Ubuntu and now, when i go to sysinfo, it says I have two cores. 

The output of cat /proc/cpuinfo is now the following

```
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 14
model name      : Genuine Intel(R) CPU           T2400  @ 1.83GHz
stepping        : 8
cpu MHz         : 1000.000
cache size      : 2048 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 2
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc pni monitor vmx est tm2 xtpr
bogomips        : 3661.59
clflush size    : 64

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 6
model           : 14
model name      : Genuine Intel(R) CPU           T2400  @ 1.83GHz
stepping        : 8
cpu MHz         : 1000.000
cache size      : 2048 KB
physical id     : 0
siblings        : 2
core id         : 1
cpu cores       : 2
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc pni monitor vmx est tm2 xtpr
bogomips        : 3657.60
clflush size    : 64

```

EDIT:
I have a couple of questions. Firstly (and this is a bit paranoid), is there anything wrong with having used my laptop for 6 months using only one processor (i.e. the one processor that was active would have had to work really hard for those 6 months and the one that was inactive might be "out of shape")? Secondly, my system monitory (conky) says "Core 1: 1000 MHz" and "Core 2: 1000 MHz" but occasionally flash as 1833 MHz. What is up with that?
HI and to your first question I would not worry. The second is that the cpu's step down when not int heavy use then step up when needed. Glad you got it working and Good luck!

---

### Post by jespdj on 2008-01-02
> **intense.ego said:**
> UPDATE: I entered my BIOS, went under config and then under CPU. I noticed that there was option titled something like "Multiple Core Processing" and that it was disabled. I enabled it, booted into Ubuntu and now, when i go to sysinfo, it says I have two cores. 
...
EDIT:
I have a couple of questions. Firstly (and this is a bit paranoid), is there anything wrong with having used my laptop for 6 months using only one processor (i.e. the one processor that was active would have had to work really hard for those 6 months and the one that was inactive might be "out of shape")? Secondly, my system monitory (conky) says "Core 1: 1000 MHz" and "Core 2: 1000 MHz" but occasionally flash as 1833 MHz. What is up with that?
Good that you got it working. Strange that it was switched off in the BIOS. Did you buy that laptop new with that setting?

Don't worry about the first question. CPUs are not like your muscles, which must be used otherwise they get out of shape. There's nothing wrong with your processor when you've only used one core for six months.

And it's normal that the processor switches to a lower clock speed when it's idle. This saves power and makes the CPU not get unnecessarily hot. When you run some programs, the CPU automatically switches to a higher speed. The CPU in my laptop even has 4 speeds: 800 MHz, 1.2 GHz, 1.6 GHz and 2.0 GHz; and the one in my desktop has two speeds, 1.6 GHz and 2.4 GHz.

---

### Post by intense.ego on 2008-01-02
Thank all of you so much. I am so happy I got it working. I thought performance on Ubuntu was brilliant before dual-core and now it is going to be even better.

---

### Post by fui on 2008-01-09
I have a similar problem on a T60. 
Only on cpu is recognised.

<< cat /proc/cpuinfo >> returns:

processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Core(TM)2 CPU         T7200  @ 2.00GHz
stepping        : 6
cpu MHz         : 1000.000
cache size      : 4096 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm
bogomips        : 3992.83
clflush size    : 64

and

<< dmesg | grep CPU >> returns
[    0.000000] WARNING: NR_CPUS limit of 1 reached.  Processor ignored.
[    0.000000] Initializing CPU#0
[   14.103467] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   14.184704] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e3bd 00000000 00000001
[   14.184722] CPU: L1 I cache: 32K, L1 D cache: 32K
[   14.184725] CPU: L2 cache: 4096K
[   14.184729] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e3bd 00000000 00000001
[   14.184755] CPU: Intel(R) Core(TM)2 CPU         T7200  @ 2.00GHz stepping 06
[   15.047802] Switched to high resolution mode on CPU 0
[   17.945541] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   17.945548] ACPI: Processor [CPU0] (supports 8 throttling states)

BIOS setting are ok so, does anyone have some advice on where else I may find a solution to this..? 

Thanks in advance

---

### Post by jespdj on 2008-01-10
Look around in your dmesg output, especially around the line "WARNING: NR_CPUS limit of 1 reached. Processor ignored."

Do you have a special version of the Linux kernel installed; a version that does not support multiple CPUs? What is the output of **uname -a**?

---

### Post by fui on 2008-01-10
ah yes kernel is 2.6.22-14-386
I recall coming across a post relating to this in my earlier searches. With some extra, more educated, searching I have now found:
[https://lists.ubuntu.com/archives/ubuntu-users/2007-October/126604.html](https://lists.ubuntu.com/archives/ubuntu-users/2007-October/126604.html)

<<Thank you for responding.
> That's not quite right, you should use the -generic kernel instead of
> -386.  Install linux-generic and reboot.
As it turns out, I had *both* -386 and -generic installed, and GRUB was 
booting into -386.

So I used Synaptic to remove -386, and then rebooted, and now I'm 
happily in the -generic version. I can see in the System Monitor that I 
have a line each for CPU1 and CPU2 in my CPU usage graph.

Thank you for the tip! The computer is noticeably faster now.>>

Seems I have the same situation. I will try to fix and update on my progress...

Thanks

---

### Post by fui on 2008-01-10
Problem solved- although I seem to have some graphics issues now. Obviously something wanting the other kernel. I'll see if I can work it out.

Thanks

---

### Post by fui on 2008-01-11
So it seems I have lost my graphics card driver (Radeon Mobility X1400). But it does mean I get suspend/resume back...
I can live with that till I get smarter and can work it all out. 

Cheers

---

