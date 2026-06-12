---
title: "/proc/cpuinfo reporting CPU at 600mHz (1.6gHz processor)"
date: 2010-12-29
forum: Hardware
---

### Post by Aped on 2010-12-29
Not sure quite what's going on, but this old laptop is running fairly slowly; is there any reason for it to be underclocked by default or something? If so, what's the best route to take in undoing this nonsense? 

Out-of-the-box install, no major changes to the OS since then. A few relative chunks of info, feel free to ask for more if it seems useful:

```
me@andrew-laptop:~$ cat /proc/cpuinfo
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 13
**model name	: Intel(R) Pentium(R) M processor 1.60GHz**
stepping	: 8
**cpu MHz		: 600.000**
cache size	: 2048 KB
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 2
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov clflush dts acpi mmx fxsr sse sse2 ss tm pbe nx up bts est tm2
bogomips	: 1197.10
clflush size	: 64
```

And a link to lshw -html: [http://slurpm.com/output_laptop.html](http://slurpm.com/output_laptop.html)

Thanks in advance for any and all help.

---

### Post by wojox on 2010-12-29
Right click the top panel and Add to Panel 

CPU Frequency Scaling Monitor. 

You can adjust it from there. It defaults at on demand.

---

### Post by Aped on 2010-12-29
Wow that's so simple and elegant, thanks. I'd been looking at some cpufreq stuff which was not working well, thanks a ton man.

---

### Post by wojox on 2010-12-29
Your welcome, man.

---

### Post by rohit6699 on 2011-06-15
Hi,
Just tried to add to the panel
"CPU frequency scaling".

It errors out saying that 
"CPU frequency scaling is unsupported"

My ACPI is switched off since it is a dual core processor and ubuntu hangs if acpi is on.

Even thought the ACPI is off still it is detecting only one processor.
Found out using the command cat /proc/cpuinfo

~~~~~~~Posting the output~~~~~~~~
cat /proc/cpuinfo
processor    : 0
vendor_id    : GenuineIntel
cpu family    : 15
model        : 4
model name    : Intel(R) Pentium(R) D  CPU 2.66GHz
stepping    : 7
cpu MHz        : 2666.451
cache size    : 1024 KB
physical id    : 0
siblings    : 1
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
flags        : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc up pebs bts pni dtes64 monitor ds_cpl tm2 cid cx16 xtpr lahf_lm
bogomips    : 5332.90
clflush size    : 64
cache_alignment    : 128
address sizes    : 36 bits physical, 48 bits virtual
power management:
~~~~~~~~~~~~~~END~~~~~~~~~~~~~~~

Help!!!!!!!!! Pleaseeee !!!!!!

---

### Post by Yellow Pasque on 2011-06-15
Have you tried a BIOS update?

---

