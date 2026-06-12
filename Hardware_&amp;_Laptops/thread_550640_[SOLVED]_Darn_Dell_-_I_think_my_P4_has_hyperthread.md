---
title: "[SOLVED] Darn Dell - I think my P4 has hyperthreading what do u think?"
date: 2007-09-14
forum: Hardware &amp; Laptops
---

### Post by nowshining on 2007-09-14
cat /proc/cpuinfo has the flag ht


processor       : 0
vendor_id       : GenuineIntel
cpu family      : 15
model           : 2
model name      : Intel(R) Pentium(R) 4 CPU 2.66GHz
stepping        : 9
cpu MHz         : 2660.094
cache size      : 512 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe up cid xtpr
bogomips        : 5324.60
clflush size    : 64



and cpuid shows

 eax in    eax      ebx      ecx      edx
00000000 00000002 756e6547 6c65746e 49656e69
00000001 00000f29 00010809 00004400 bfebfbff
00000002 665b5101 00000000 00000000 007b7040
80000000 80000004 00000000 00000000 00000000
80000001 00000000 00000000 00000000 00000000
80000002 20202020 20202020 20202020 6e492020
80000003 286c6574 50202952 69746e65 52286d75
80000004 20342029 20555043 36362e32 007a4847

Vendor ID: "GenuineIntel"; CPUID level 2

Intel-specific functions:
Version 00000f29:
Type 0 - Original OEM
Family 15 - Pentium 4
Extended family 0
Model 2 - 
Stepping 9
Reserved 0

Brand index: 9 [not in table]
Extended brand string: "              Intel(R) Pentium(R) 4 CPU 2.66GHz"
CLFLUSH instruction cache line size: 8
Hyper threading siblings: 1

Feature flags bfebfbff:
FPU    Floating Point Unit
VME    Virtual 8086 Mode Enhancements
DE     Debugging Extensions
PSE    Page Size Extensions
TSC    Time Stamp Counter
MSR    Model Specific Registers
PAE    Physical Address Extension
MCE    Machine Check Exception
CX8    COMPXCHG8B Instruction
APIC   On-chip Advanced Programmable Interrupt Controller present and enabled
SEP    Fast System Call
MTRR   Memory Type Range Registers
PGE    PTE Global Flag
MCA    Machine Check Architecture
CMOV   Conditional Move and Compare Instructions
FGPAT  Page Attribute Table
PSE-36 36-bit Page Size Extension
CLFSH  CFLUSH instruction
DS     Debug store
ACPI   Thermal Monitor and Clock Ctrl
MMX    MMX instruction set
FXSR   Fast FP/MMX Streaming SIMD Extensions save/restore
SSE    Streaming SIMD Extensions instruction set
SSE2   SSE2 extensions
SS     Self Snoop
HT     Hyper Threading
TM     Thermal monitor
31     reserved

TLB and cache info:
51: Instruction TLB: 4KB and 2MB or 4MB pages, 128 entries
5b: Data TLB: 4KB and 4MB pages, 64 entries
66: 1st-level data cache: 8KB, 4-way set assoc, 64 byte line size
40: No 2nd-level cache, or if 2nd-level cache exists, no 3rd-level cache
70: Trace cache: 12K-micro-op, 4-way set assoc
7b: 2nd-level cache: 512KB, 8-way set assoc, sectored, 64 byte line size

.............

I tried HT in another post a bit of quickness but no much - prob. me tho...  also the Dell Bios on my rig show no way to enable it, however like I: said cpuinfo show it can ht.. So my guess is that Dell disable it. Anyway to try instead of in the grub list inputting ht-on ???

---

### Post by nowshining on 2007-09-14
someone has the same cpu with HT

x86 Family 15 Model 2 Stepping 9 GenuineIntel 

same as mine  but mine's underclocked or clocked lower

[http://www.driverforum.com/graphics5/11815.html](http://www.driverforum.com/graphics5/11815.html)

darn it I get it working.. :P

---

### Post by PmDematagoda on 2007-09-14
I have an EM64T HT Pentium 4 processor here's my info:-

L2 cache:- 1024 kb

L1 cache:- 16 kb

Speed:- 3.2 Ghz

Code name:- Prescott

The model is:- Family 15 model 4 level 1

It shows in my system to be 32 bit, but it can support 64 as well. And HT can be turned on or off in my BIOS which is of an Intel Mainboard.:)

The problem with you may be because your processor doesn't have HT or your mainboard by some chance doesn't support HT. I've had no problems because I specifically asked for HT and they gave me a suitable mainboard for the processor(I built my desktop).

---

### Post by nowshining on 2007-09-14
well my Bios doesn't have it where I can enable it and since the flags are there I do believe Dell must of locked it somehow, maybe I could get another bios, lolz anyway Wow yours is the best anyway a meg of L2 cache and L1 cache double mine, wow oh that's right you Bought urs right??? sepearately ??

edit: unless of course I am reading it wrong.. and I never heard of the motherboard not supporting HT..

---

### Post by Kingsley on 2007-09-14
You mean "cat /proc/cpuinfo"

---

### Post by nowshining on 2007-09-14
cpuinfo is installed by default and I installed cpuinfo and oh lolz i'll edit that - edited

---

### Post by sr20ve on 2007-09-14
The Dell bios should have an option under "CPU information," for "Logical Processor," which can be set to Enabled or Disabled, that is for the hyperthreading.

---

### Post by SunnyRabbiera on 2007-09-14
me I cannot tell the difference when I have hyperthreading on or off, there is no real difference to me.

---

### Post by nowshining on 2007-09-15
> **SunnyRabbiera said:**
> me I cannot tell the difference when I have hyperthreading on or off, there is no real difference to me.

I might have logical processor, I don't know tho.. :) prob. not...

---

### Post by K.Mandla on 2007-09-15
Moved to Hardware and Laptops. ;)

---

### Post by nowshining on 2007-09-15
k, thanks I guess - :) just found a bug or feature of gutsy sessions, If I do something with a astrick in front of the name I don't have to click the Check box, I meant for the astrick to make it show first or startup first...

example..

*overclock

that wouldn't need a check mark next to it, first updates tho..

:)

oh and last time ipblock blocked me out - grrrr 

For the last post in the biso I was thinking of the processor ID, :P and no not in this bios - have the latest... (just got finished overclocking my GPU and UnderClocking the memory so both match - and make them stay at least on login)

---

### Post by nowshining on 2007-09-15
strange i found a link and it said that enable HT and it wa s diff. well i did and rebooted everything is a bit faster esp. during bootup after the grub menu- no 2 processors in monitor, however duing boot I did notice something diff. and that was WACOM or something it was centered lolz.. :)

ht=on did nothing, however

acpi=ht

where ht=on was and changed them all again rebooted and yay everything is bit faster - or It's just me :P I stayed up all night.. hehe :D

so it really did something or I'm just waking up or some energy kicked in or I'm way too tired, one or the other.. :)

[http://www.linuxquestions.org/questions/showthread.php?s=&postid=1413211](http://www.linuxquestions.org/questions/showthread.php?s=&postid=1413211)

saw this

```

acpi=ht means enable hyperthreading for your processor

```

applied that :)

---

### Post by nowshining on 2007-09-15
whoa the shared pictures jpg folder I open up didn't take as long to show them all in preview form and opening one up in by default eye of gnome = speed - improved.. :)


edit: now for getting the Clock speed right on this graphic card. :) or so....gotta change regular  top 3d speed - too high over like 300 has stability problems most likely because of no fan just heat sink as the settings say it can go up to 500 or so..Anyway oh...

---

### Post by nowshining on 2007-09-15
by the way the performance on mine is rougly small, but still worth it to me also it said which it never said before (I caught it this time - payed more attention)

Doing Wacom Setup


:) whatever that is..

---

### Post by nowshining on 2007-09-15
WACOM is a Tablet PC input thing (Google - WACOM) or something, odd tho it would only come up doing that and the small bit of speed improvement on a desktop when I did that is a MYSTERY to me. :P

---

### Post by nowshining on 2007-09-15
who google must of just indexed this site after that post - doing a google search on  with the quotes "Doing WACOM Setup" brings up this forum and this page.. ot an hour ago - still.. funny..

---

### Post by nowshining on 2007-09-15
solution to get this baby performance wise was to do the following

in grub add acpi=ht

and in the kernel 

[http://mandrivausers.org/lofiversion/index.php/t31192.html](http://mandrivausers.org/lofiversion/index.php/t31192.html)

and going in and changing

CONFIG_SCHED_SMT=y 

to

CONFIG_SCHED_SMT=n


then a reboot

seemed to help the hiccups at least a great bit - still does however but not as bad. Yes each one is in it's own kernel... :) and if you updaed to many like me find the current one.. lolz..

---

### Post by nowshining on 2007-09-15
oh and from

[http://www.ducea.com/2006/06/23/linux-tips-how-to-find-out-if-a-your-cpu-supports-ht-hyper-threading/](http://www.ducea.com/2006/06/23/linux-tips-how-to-find-out-if-a-your-cpu-supports-ht-hyper-threading/)


```


Inside the flags section we are looking for a &#8220;ht&#8221; flag. If it is present, this means that the system supports HT.
Let&#8217;s look on another sample taken from a Pentium4 CPU (the un-needed infos were removed):

```

so my system does - however it's Dells Fault for not Bios enabling it.. Anyway that still makes my computer Ultra Rare.. :P

---

