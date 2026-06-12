---
title: "How do I read the information that &quot;cat /proc/cpuinfo&quot; gives?"
date: 2006-12-31
forum: Hardware &amp; Laptops
---

### Post by angkel07 on 2006-12-31
I ran the command "cat /proc/cpuinfo" and I can't understand what it says. Can someone give me the info for me? Here's what came up after executing the command:```
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 15
model           : 4
model name      : Intel(R) Pentium(R) 4 CPU 2.66GHz
stepping        : 1
cpu MHz         : 2668.026
cache size      : 1024 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 5
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm pni monitor ds_cpl tm2 cid cx16 xtpr
bogomips        : 5337.58

```

Thank you.

---

### Post by 23meg on 2006-12-31
Is there any specific information you're looking for?

---

### Post by angkel07 on 2006-12-31
I need to know what does each item mean, namely, processor, vendor_id, cpu family, model, model name, stepping, cpu MHz, cache size, fdiv_bug, hlt_bug, f00f_bug, coma_bug, fpu, fpu_exception, cpuid level, wp, flags and bogomips. The only items that I can understand are vendor_id, model name, cpu MHz and cache size. I need an explanation for the rest. Thank you.

---

### Post by malathia on 2006-12-31
Is there any particular reason? or just for personal knowledge's sake?

---

### Post by angkel07 on 2006-12-31
It's for knowledge's sake. I just wanted to know what's the capabilities of my CPU. Thank you.

---

### Post by po0f on 2006-12-31
angkel07,

You're going to have to google those flags.  Some of them should be obvious (acpi, mmx, sse, sse2) but the others you'll have to look up.

---

### Post by malathia on 2006-12-31
Give me just a bit, I'm compiling an answer to your question with somewhat appropriate links to point you on your way. You'll have your full answer momentarily.

---

### Post by angkel07 on 2006-12-31
I was just asking what does the parameters mean, I wasn't asking you to analyze the info. I already know flags. The rest is what I don't know.

---

### Post by malathia on 2006-12-31
there is no analyzation, you're asking basically what every aspect of that output means. If you know the flags, how do you not know how to read the cache size? it's spelled out. Just allow me to finish this up and you'll have your answer. 

Were you being an impatient or am I misreading?

---

### Post by angkel07 on 2006-12-31
> 
I need to know what does each item mean, namely, processor, vendor_id, cpu family, model, model name, stepping, cpu MHz, cache size, fdiv_bug, hlt_bug, f00f_bug, coma_bug, fpu, fpu_exception, cpuid level, wp, flags and bogomips. **The only items that I can understand are vendor_id, model name, cpu MHz and cache size.** I need an explanation for the rest. Thank you.

Read.... =.=

---

### Post by malathia on 2006-12-31
Okay, Corrected the formatting. Should be more readable now. Again, any errors in information, please let me know.


Processor:  
	Linux's denotation of what processor, similar to the naming of all devices under linux.
VendorID: 
	The vendor of your processor. Intel/AMD/Cyrix/etc.
CacheSize: 
	The cache built into your CPU.
			
		For more information see:
			[http://en.wikipedia.org/wiki/CPU_cache](http://en.wikipedia.org/wiki/CPU_cache)

CPU family: 
		If I'm not mistaken is an indexed indication of your processor's architecture. I couldn't 			find a succinct list of the number to architecture correspondence, so I may be wrong.

Model and Model Name: 

		From what I've read, Model number appears to come from the BIOS on your mobo, not 			not necessarily indicating the appropriate CPU. Thus, from what I know at the 				moment, Model Name is the more important in most any application. 

The *_Bug Entries:

		The *_bug section details whether or not your CPU is susceptible to some well known 			processor bugs. Information on the bugs specifically referenced in your /proc/cpuinfo  			follows:

			f00f_bug: [http://www.bio.net/bionet/mm/bio-soft/1998-January/018153.html](http://www.bio.net/bionet/mm/bio-soft/1998-January/018153.html)
			hlt_bug: [http://listserver.uk.freebsd.org/pipermail/freebsd-users/2000-October/002486.html](http://listserver.uk.freebsd.org/pipermail/freebsd-users/2000-October/002486.html)
			FDIV bug: [http://en.wikipedia.org/wiki/Pentium_FDIV_bug](http://en.wikipedia.org/wiki/Pentium_FDIV_bug)
			Coma Bug: 
				The Cyrix coma bug is a design flaw in Cyrix 6x86, 6x86L, and early 					6x86MX processors that allows a non-privileged program to completely 					lock the computer. (basically F0 0F bug for Cyrix)


Stepping:

	In addition to the CPU's model number of letter, the Processor Revision reveals one 			other bit of information -- a CPU's Stepping. As a CPU model matures, the chip-maker 			discovers little ways to make it easier to manufacture. It may also make changes to the 			CPU design to fix errors, or make the chip more reliable. Each of these changes is given 			a Stepping number, perhaps because each new version is a new step in the evolution of 			the chip design.


FPU: 
	Whether or not your processer has a Floating Point Unit &#8211; (Math Co-processor)

FPU Exception: 
	I believe this is to show whether or not your processor respects the IEEE specifications
	on flagging and trapping Floating Point Exceptions
	See following for more information:
		[http://www.unet.univie.ac.at/aix/aixprggd/genprogc/floating-point_except.htm](http://www.unet.univie.ac.at/aix/aixprggd/genprogc/floating-point_except.htm)

CPUID: 

	This is heavily tied with the flags also listed in the /proc/cpuinfo
	See following link:
		[http://grafi.ii.pw.edu.pl/gbm/x86/cpuid.html](http://grafi.ii.pw.edu.pl/gbm/x86/cpuid.html)

BogoMips: 
	In short, it is Linux's representation of the clock speed for your processor
	see: 
		[http://en.wikipedia.org/wiki/BogoMips](http://en.wikipedia.org/wiki/BogoMips)

---

### Post by malathia on 2006-12-31
> **angkel07 said:**
> Read.... =.=

May I also point out that, though you are correct, I didn't read to the end, you have a confusion of statements, because you ask in the beginning what each one means, listing those that you list later that you know the meaning of.

Whatever, it's of little consequence, I just don't really see why you were being impatient when I was doing you a favor by answering your question.

Anyway, whatever, no hard feelings. I'm assuming that I'm feeling heightened agitation from being at work for over 8 hours already.

Kind regards,

  -Malathia

---

