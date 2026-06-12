---
title: "Centrino Duo T2300: Incorrect freqs, or just paranoia?"
date: 2006-10-11
forum: Hardware &amp; Laptops
---

### Post by veXxv on 2006-10-11
Hey, guys. I put Dapper on my laptop (HP Pavilion dv1000 series) a few days back, and so far it's going relatively well (compared to the other adventures I've had with Linux, at least :P).

However! I'm a bit confused about the info I get from /proc/cpuinfo on my CPU (Centrino Duo T2300). I've searched around to what seems to be no avail...

```

processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 14
model name      : Genuine Intel(R) CPU           T2300  @ 1.66GHz
stepping        : 8
cpu MHz         : 1663.164
cache size      : 2048 KB
physical id     : 0
siblings        : 1
core id         : 255
cpu cores       : 1
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx pni monitor vmx est tm2 xtpr
bogomips        : 2053.36

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 6
model           : 14
model name      : Genuine Intel(R) CPU           T2300  @ 1.66GHz
stepping        : 8
cpu MHz         : 1663.164
cache size      : 2048 KB
physical id     : 1
siblings        : 1
core id         : 255
cpu cores       : 1
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx pni monitor vmx est tm2 xtpr
bogomips        : 2053.36

```

Now, as far as I remember under XP, the frequency for CPU1 was less than what came up for CPU0. So could it be that Linux is unintentionally overclocking CPU1 (because I have noticed that my computer likes to heat up a bit more under Dapper than XP)? Or was Windows underclocking it? Or am I totally wrong in all respects and just a silly newb? :P

Thanks for any and all help, guys!

---

### Post by mdwuznik on 2006-10-11
That's more of paranoia than problem :)
Dual-core processors are clocked by _one_ frequency (one for all cores, 
changed simultanously). If some tool states sth else, it's thi tool error.

Happy CoreDuoing
Michal

---

### Post by veXxv on 2006-10-11
Ah, okay. :D

I've never had to deal with more than one processor, so I was unfamiliar with that.

Thanks so much, though. This forum has proven to be absolutely invaluable.

---

