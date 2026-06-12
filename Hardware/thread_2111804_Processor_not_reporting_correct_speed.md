---
title: "Processor not reporting correct speed"
date: 2013-02-03
forum: Hardware
---

### Post by vanquishedangel on 2013-02-03
Ok here goes, my system specs: 

HP dc5750
8 gb ram
2.5 ghz processor Athlon 64 X2 Dual-Core 4800+
ATI radeon hd 6450 (1 gig vram)

here is a link to the specs [http://h18000.www1.hp.com/products/quickspecs/12546_na/12546_na.html](http://h18000.www1.hp.com/products/quickspecs/12546_na/12546_na.html)

The problem I noticed was that it booted slow, so I looked it up and came across the command cat /proc/cpuinfo | head -10
when I ran it I got this

processor	: 0
vendor_id	: AuthenticAMD
cpu family	: 15
model		: 107
model name	: AMD Athlon(tm) 64 X2 Dual Core Processor 4800+
stepping	: 1
cpu MHz		: 1000.000
cache size	: 512 KB
physical id	: 0
siblings	: 2

Also when I run system profiler and benchmark under processor it shows this :

AMD Athlon(tm) 64 X2 Dual-Core Processor 4800+ 2400.00MHz
AMD Athlon(tm) 64 X2 Dual-Core Processor 4800+ 2400.00MHz

but it used to say in 12.04:

AMD Athlon(tm) 64 X2 Dual-Core Processor 4800+ 1000.00MHz
AMD Athlon(tm) 64 X2 Dual-Core Processor 4800+ 1000.00MHz

I am not sure when this changed, I ignored it because I felt that my games were working so I left it lol. Could this be from a program Lubuntu installs maybe?

When I run cat /proc/cpuinfo I get this:

processor	: 0
vendor_id	: AuthenticAMD
cpu family	: 15
model		: 107
model name	: AMD Athlon(tm) 64 X2 Dual Core Processor 4800+
stepping	: 1
cpu MHz		: 2500.000
cache size	: 512 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 2
apicid		: 0
initial apicid	: 0
fpu		: yes
fpu_exception	: yes
cpuid level	: 1
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow rep_good nopl pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch lbrv
bogomips	: 4987.85
TLB size	: 1024 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 40 bits physical, 48 bits virtual
power management: ts fid vid ttp tm stc 100mhzsteps

processor	: 1
vendor_id	: AuthenticAMD
cpu family	: 15
model		: 107
model name	: AMD Athlon(tm) 64 X2 Dual Core Processor 4800+
stepping	: 1
cpu MHz		: 2500.000
cache size	: 512 KB
physical id	: 0
siblings	: 2
core id		: 1
cpu cores	: 2
apicid		: 1
initial apicid	: 1
fpu		: yes
fpu_exception	: yes
cpuid level	: 1
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow rep_good nopl pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch lbrv
bogomips	: 4987.85
TLB size	: 1024 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 40 bits physical, 48 bits virtual
power management: ts fid vid ttp tm stc 100mhzsteps

That make it more confusing because one says 1000.00MHz, another says 2400.00MHz and the last says 2500.00MHz. The issue is this computer is booting very slow, slower than an hp dc7100 with a intel 3.8ghz HT single core, 1.5 gigs ram (slow speed ram), ati 4850, but it seems a lil longer on applications to.

---

### Post by sanderj on 2013-02-03
Isn't that just the *actual* CPU frequency? Remember: the OS will adjust the freq to what's needed

---

### Post by vanquishedangel on 2013-02-05
> **sanderj said:**
> Isn't that just the *actual* CPU frequency? Remember: the OS will adjust the freq to what's needed

True but then all commands should report the same frequency, and then it should either be the max frequency (been my experience in linux) or the same one at least I would think. I am semi-not really familiar with cpufreq and programs like it may be the cause, just usually not this different in results, also my boot and application time I would think should still be faster.

---

### Post by Doyle33 on 2013-02-05
You can check if cpu frequency scaling is enabled with the command "/sbin/service cpuspeed status". I think by default the ondemand governor is used.  With cpuspeed you can also control your cpuspeed manually. A alternative tool is cpufrequtils, which is in the repos but not installed by default.  In case if the cpu is too hot it will also disable higher frequencies. Install lm_sensors, run sensors-detect and then use sensors to see if the temperatures are not too high.




[bigwigjackets.com]("http://www.bigwigjackets.com/michael-jackson-bad-tour-jacket.html") // [Resident evil jacket]("http://www.bigwigjackets.com/resident-evil-jacket.html") // [shia labeouf jacket]("http://www.bigwigjackets.com/shia-labeouf-jacket.html")

---

### Post by vanquishedangel on 2013-02-09
bash: /sbin/service: No such file or directory

That is what appears in the terminal with the command

thank you for you responces guys, I would like to get this worked out as soon as I can

---

### Post by leclerc65 on 2013-02-09
I had same problem.
An update to a more recent Bios fixed it.

---

### Post by Yellow Pasque on 2013-02-09
> **vanquishedangel said:**
> True but then all commands should report the same frequency.

False. It depends on what speed your CPU is running at when you run the command. There's nothing problematic/worrisome/wrong with the output you've shown.

---

### Post by vanquishedangel on 2013-03-09
ty very much for that info

---

