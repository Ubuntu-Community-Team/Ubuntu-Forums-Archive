---
title: "Cpu"
date: 2009-03-22
forum: Hardware
---

### Post by flyingsliverfin on 2009-03-22
how do I find out what CPU I have (32 or 64 bit)

its a pentium 4 (2 seperate processors, don't know if that makes a difference), but when I want to install 64 bit systems virtually, they complain that the computer is not 64 bit.

im also a bit confused about what the difference between 64 and 32 bit systems and the what runs on what (are they cross-compatible?)

---

### Post by millsy_c on 2009-03-22
> **flyingsliverfin said:**
> how do I find out what CPU I have (32 or 64 bit)

its a pentium 4 (2 seperate processors, don't know if that makes a difference), but when I want to install 64 bit systems virtually, they complain that the computer is not 64 bit.

im also a bit confused about what the difference between 64 and 32 bit systems and the what runs on what (are they cross-compatible?)

Do you mean in a virtual machine? If so I really don't know much about those, but what I do know of them is that they are only 32bit. If I'm wrong could someone please correct me?

It's worth a google to get a more in-depth response about your second question, but in a nutshell a 64bit system can access more RAM than a 32bit system (which is limited to around 4gb of RAM).
32bit operating systems and programs can run on a 64bit machine, but 64bit applications and operating systems can NOT run on a 32bit machine.
If you are unable to install a 64bit operating system it means that you almost certainly have a 32bit processor. If you have no need to access more than 4gb ram then there really is no need to go 64bit.

---

### Post by flyingsliverfin on 2009-03-23
i mean in a virtual machine ,yes, sory for not making it clearer. 

do you know how i find out if my computer is 64 or bit or not? My brother thinks that 64 bit systems are faster (can't agree or disagree, never tried it) also, is it possible for me to upgrade (next time) from a 32 bit t o 64 bit system while upgrading the os from 8.10 ti 9.__?

---

### Post by cariboo on 2009-03-23
Open a terminal and  type:

```
cat /proc/cpuinfo
```

it shuld ouprut something like this:

```
processor	: 0
vendor_id	: AuthenticAMD
cpu family	: 15
model		: 75
model name	: AMD Athlon(tm) 64 X2 Dual Core Processor 3800+
stepping	: 2
cpu MHz		: 2009.332
```

there is a lot more to the output.

Or even easier go to System-->Administration-->System Monitor and click the system tab. See the screenshot.

Jim

---

### Post by flyingsliverfin on 2009-03-25
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 15
model		: 4
model name	: Intel(R) Pentium(R) 4 CPU 3.00GHz
stepping	: 3
cpu MHz		: 2992.435
cache size	: 2048 KB
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
cpuid level	: 3
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc pebs bts pni monitor ds_cpl est cid cx16 xtpr
bogomips	: 5984.87
clflush size	: 64
power management:

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 15
model		: 4
model name	: Intel(R) Pentium(R) 4 CPU 3.00GHz
stepping	: 3
cpu MHz		: 2992.435
cache size	: 2048 KB
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
cpuid level	: 3
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc pebs bts pni monitor ds_cpl est cid cx16 xtpr
bogomips	: 5985.00
clflush size	: 64



which one tells me if it is 64 or 32 bit?

oh and just a question, what is stepping, I heard this mentioned in another thread

---

