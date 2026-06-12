---
title: "Problems with Core Duo and Edgy Eft"
date: 2006-12-29
forum: Hardware &amp; Laptops
---

### Post by gbraad on 2006-12-29
I run Edgy Eft on a Sony VAIO SZ2VP laptop. Since the laptop has a Core Duo processor, I should be able to run it as an SMP processor. With Dapper Drake I did... but after update I had to reconfigure it. Seems I would need to use the generic kernel for this. When I do, I still am not able to do so. (System has been upgraded from Dapper to Edgy, although quite some time ago)

uname shows:
Linux defiance 2.6.17-10-generic #2 SMP Tue Dec 5 22:28:26 UTC 2006 i686 GNU/Linux

/cat/cpuinfo
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 14
model name	: Genuine Intel(R) CPU           T2600  @ 2.16GHz
stepping	: 8
cpu MHz		: 2167.262
cache size	: 2048 KB
physical id	: 0
siblings	: 1
core id		: 255
cpu cores	: 1
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc up pni monitor vmx est tm2 xtpr
bogomips	: 4340.97

On the windows partition it does show 2 cores... and there is no option in the BIOS to turn the dual core functionality off... Hope anyone has some idea.

Thanks in advance,


Gerard

---

### Post by gbraad on 2006-12-29
[RESOLVED] Downgrading to dapper drake didn't work, found out BIOS settings were corrupted; BIOS doesn't provide a disable/enable functionality dual core. ](*,) 
Cores were properly detected by another OS, just one core was disable due to a BIOS error.

---

