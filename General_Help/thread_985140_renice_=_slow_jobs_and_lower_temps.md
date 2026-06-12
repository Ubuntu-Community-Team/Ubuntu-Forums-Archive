---
title: "renice = slow jobs and lower temps"
date: 2008-11-17
forum: General Help
---

### Post by mark_a_kessler on 2008-11-17
hello all,
this is my first post here and I'm hoping it's not wrongly placed.

I've been using renice for years to run jobs (simulations) in the background.  I noticed yesterday that renicing my jobs gives me a 15 degree drop in CPU temp.  This led me to check the processor usage, which was at 100% on all four processors.  However, when I checked the actual time it took to run a simulation, it turned out to be twice as long as when the jobs were not reniced.  This held even when I only ran one simulation on a 4 processor AMD phenom machine (only one processor was at 100%).  I tried the same thing on a Intel Q9550 and only saw a 25% increase in run time with the job niced.

Any thoughts?  Why does top show 100% usaged when it seems only 50% of the processor capability is being used?

thanks,
mark

---

### Post by happyhamster on 2008-11-17
Perhaps there's cpu frequency-scaling going on. You can check with the command:

cat /proc/cpuinfo


[edit: And take a look at System-->Administration-->Services to see if you have a cpu frequency manager running. And if so, which one?]

---

### Post by psusi on 2008-11-17
Yes, if you set the nice value to the lowest priority, then the processor is considered idle while running it by the power management stuff so it puts the cpu in low power mode.

---

### Post by mark_a_kessler on 2008-11-17
thank you for the help.  Is there any way to nice a job, but not put a processor in low power mode?

---

### Post by mark_a_kessler on 2008-11-17
both machines are running the CPU Frequency manager powernowd.  Here is the rather extensive output from the command you suggested, but it doesn't change when I have a niced job running.  What should I be looking for and is it something that can be altered.  BTW, the job slows down by roughly the same amount even if I only renice the job to 1.

processor	: 0
vendor_id	: AuthenticAMD
cpu family	: 16
model		: 2
model name	: AMD Phenom(tm) 9600 Quad-Core Processor
stepping	: 2
cpu MHz		: 1150.000
cache size	: 512 KB
physical id	: 0
siblings	: 4
core id		: 0
cpu cores	: 4
apicid		: 0
initial apicid	: 0
fpu		: yes
fpu_exception	: yes
cpuid level	: 5
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc rep_good nopl pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs
bogomips	: 4600.14
TLB size	: 1024 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 48 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate

processor	: 1
vendor_id	: AuthenticAMD
cpu family	: 16
model		: 2
model name	: AMD Phenom(tm) 9600 Quad-Core Processor
stepping	: 2
cpu MHz		: 1150.000
cache size	: 512 KB
physical id	: 0
siblings	: 4
core id		: 3
cpu cores	: 4
apicid		: 1
initial apicid	: 3
fpu		: yes
fpu_exception	: yes
cpuid level	: 5
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc rep_good nopl pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs
bogomips	: 4600.40
TLB size	: 1024 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 48 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate

processor	: 2
vendor_id	: AuthenticAMD
cpu family	: 16
model		: 2
model name	: AMD Phenom(tm) 9600 Quad-Core Processor
stepping	: 2
cpu MHz		: 1150.000
cache size	: 512 KB
physical id	: 0
siblings	: 4
core id		: 1
cpu cores	: 4
apicid		: 2
initial apicid	: 1
fpu		: yes
fpu_exception	: yes
cpuid level	: 5
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc rep_good nopl pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs
bogomips	: 4600.25
TLB size	: 1024 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 48 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate

processor	: 3
vendor_id	: AuthenticAMD
cpu family	: 16
model		: 2
model name	: AMD Phenom(tm) 9600 Quad-Core Processor
stepping	: 2
cpu MHz		: 1150.000
cache size	: 512 KB
physical id	: 0
siblings	: 4
core id		: 2
cpu cores	: 4
apicid		: 3
initial apicid	: 2
fpu		: yes
fpu_exception	: yes
cpuid level	: 5
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc rep_good nopl pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs
bogomips	: 4600.26
TLB size	: 1024 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 48 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate

---

### Post by happyhamster on 2008-11-17
- A good try would be to run powernowd with the -n option. From the powernowd manual pages:

> 
-n     Include nice’d processes in calculations.


- You can make that change in the file /etc/default/powernowd

gksudo gedit /etc/default/powernowd

- In my case, the file looks like this:

> 
#default file for powernowd, see man 1 powernowd
# 
# Options
OPTIONS="-q"


- Change that into:

> 
#default file for powernowd, see man 1 powernowd
# 
# Options
OPTIONS="-q -n"


- Save and exit the text editor. Then restart powernowd:

sudo /etc/init.d/powernowd restart

- And check if anything changed for the better. Good luck, and keep us informed.


> 
hello all,
this is my first post here
Welcome to the forums, BTW :)

---

### Post by mark_a_kessler on 2008-11-20
hello happyhamster, many thanks for the advice.  I set the -n flag and the test job is runing as I type.  Should be done by the time I finish.

I'm really sorry for not getting back to you right away.  I forgot to set my forum account up to email me when threads are posted to, so I got busy with other fires and this slipped my mind.  Please don't take this to mean I don't greatly appreciate the help, I really do.

Beautiful, that did the trick.  I'm going to have to go read the man page, and leave myself a note somewhere to make this change on all my machines.  Thanks again for your help.

Cheers!
mark

---

