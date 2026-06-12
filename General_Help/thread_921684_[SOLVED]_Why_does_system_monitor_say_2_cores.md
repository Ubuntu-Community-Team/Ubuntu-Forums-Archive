---
title: "[SOLVED] Why does system monitor say 2 cores?"
date: 2008-09-16
forum: General Help
---

### Post by x300 on 2008-09-16
I've got an old Intel Pentium 4 CPU operating at 3.4GHz. Why does Gnome System Monitor say that it's dual core? (see attached screen shots)

I really don't understand! Can anyone explain?

Thanks

---

### Post by mikewhatever on 2008-09-16
Can you post the output of the following command:

> cat /proc/cpuinfo

---

### Post by x300 on 2008-09-16
Sure.

me@stat:~$ cat /proc/cpuinfo 
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 15
model		: 3
model name	: Intel(R) Pentium(R) 4 CPU 3.40GHz
stepping	: 4
cpu MHz		: 3397.103
cache size	: 1024 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 1
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 5
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe constant_tsc pebs bts sync_rdtsc pni monitor ds_cpl cid xtpr
bogomips	: 6800.37
clflush size	: 64

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 15
model		: 3
model name	: Intel(R) Pentium(R) 4 CPU 3.40GHz
stepping	: 4
cpu MHz		: 3397.103
cache size	: 1024 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 1
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 5
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe constant_tsc pebs bts sync_rdtsc pni monitor ds_cpl cid xtpr
bogomips	: 6794.48
clflush size	: 64

---

### Post by liquidfunk on 2008-09-16
Is it possible that it's a P4 with HT, hyper-threading, which is the old school version of dual core.

---

### Post by x300 on 2008-09-16
I have no idea... I bought it 2004-05-24 if it's of any help. And I see in my papers that it's an Intel Pentium 4 "Prescott", whatever that is.

---

### Post by mikewhatever on 2008-09-16
Odd, I really don't know. How old is it? Could it be a Pentium D?

---

### Post by shad0w_walker on 2008-09-16
In the flags section I see HT, which I assume refer to hyper threading.

---

### Post by liquidfunk on 2008-09-16
After a bit of Googling, I found out that yes, it is a Pentium 4 that has Hyperthreading. 

 The Intel site says: "Hyper-threading enables multi-threaded software applications to execute two software threads in parallel, thereby improving system responsiveness." 

 So from what it looks like is a Single Core processor, with 2 threads that process the information for certain things. So its kind of a single core cut into 2 halves. 

 I had one in my older laptop.

---

### Post by x300 on 2008-09-16
Thanks, that explains a lot :)

Didn't know that my old processor were hightech!

---

### Post by liquidfunk on 2008-09-16
Your welcome! Every processor is High tech, I don't believe in rubbish hardware.

---

