---
title: "Hardy Heron shows only one CPU - Toshiba A120"
date: 2008-05-07
forum: Hardware
---

### Post by misio on 2008-05-07
Hi, I would be really grateful if someone found the time to help me out on this.

I have a Toshiba Satellite pro A120 with a centrino duo T2400 processor but Hardy Heron does not recognize the dual cores.

Running ```
uname -a
``` results in
> Linux leon-laptop 2.6.24-16-generic #1 SMP Thu Apr 10 13:23:42 UTC 2008 i686 GNU/Linux

Which from what I have read is a i686 and SMP kernel that should be okay for this processor.


running ```
cat /proc/cpuinfo
``` gives me
> 
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 14
model name	: Genuine Intel(R) CPU           T2400  @ 1.83GHz
stepping	: 8
cpu MHz		: 1828.800
cache size	: 2048 KB
physical id	: 0
siblings	: 1
core id		: 0
cpu cores	: 1
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe constant_tsc up arch_perfmon bts pni monitor vmx est tm2 xtpr
bogomips	: 3662.58
clflush size	: 64

Running top, then pressing 1 again shows me one CPU.

I ran ```
dmesg | less
``` and the relevant result seems to be here

> [    6.423280] SMP alternatives: switching to UP code
[    6.424909] Freeing SMP alternatives: 11k freed
[    6.425009] Early unpacking initramfs... done
[    6.902242] CPU0: Intel Genuine Intel(R) CPU           T2400  @ 1.83GHz stepping 08
[    6.902259] SMP motherboard not detected.
[    7.117839] Brought up 1 CPUs

I then checked the BIOS and multi core processing is switched on, I am now completely stumped. Has anyone got anything I could try?

As a side issue my laptop is also running incredibly hot and freezing up once or twice a day, but one thing at a time!

It worked perfectly under XP but I really dont want to go back.

---

### Post by prshah on 2008-05-07
> **misio said:**
> 
I have a Toshiba Satellite pro A120 with a centrino duo T2400 processor but Hardy Heron does not recognize the dual cores.


I have the option to disable dual-core technology on my Intel motherboard BIOS... maybe you should check if it's disabled in yours? Just a suggestion... though of course it may not be this if it works fine in XP.

btw, does the XP task manager show 1 or 2 cpu graphs?

---

### Post by misio on 2008-05-08
Thanks for the reply.

The BIOS has multi core processing enabled, also two processors were visible in windows XP.

As far as the heat issue goes I have set frequency scaling to always low (just done that) so I will see if that keeps the machine a bit cooler throughout the day.

---

### Post by misio on 2008-05-08
Just an update, the frequency scaling didn't help. The system still periodically hangs. I am have re-installed XP and used wubi to create an Ubuntu drive for the purpose of further testing.

Its a shame but its my work laptop so I can't have these issues.

---

### Post by rivera151 on 2008-05-14
I'm having the same issue after upgrading to Hardy.  Gutsy showed 2 processors, Hardy shows 1.  Someone got a clue?

---

### Post by ursahoribl on 2008-06-22
Haven't upgraded to Hardy yet, but my Toshiba P25 requires selecting the generic kernel after each upgrade to use the dual cores in my processor. Just a thought.

---

