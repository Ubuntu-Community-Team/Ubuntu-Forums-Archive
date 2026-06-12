---
title: "Incorrect cpu speed"
date: 2012-05-23
forum: Hardware
---

### Post by davesbrain on 2012-05-23
This doesn't look right.   Also, XP reports it as .999.   I thought it was a 2.4.

```
davejr@desktop:~$ cat /proc/cpuinfo
processor	: 0
vendor_id	: AuthenticAMD
cpu family	: 15
model		: 12
model name	: AMD Athlon(tm) 64 Processor 3400+
stepping	: 0
cpu MHz		: 1000.000
cache size	: 512 KB
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 1
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext lm 3dnowext 3dnow up
bogomips	: 1999.68
clflush size	: 64
cache_alignment	: 64
address sizes	: 40 bits physical, 48 bits virtual
power management: ts fid vid ttp

davejr@desktop:~$ 

```

---

### Post by jjiggens on 2012-05-23
its just seeing the current clock rate. the cpu throttles down at idol. 

if you want proof. tax your cpu with a lot of work and run the same command. you will see. 

my i5 2.8 reports as a 800mhz with the same command.

---

### Post by matt_symes on 2012-05-23
Hi

Does your chip have scaling frequencies ?

Open a terminal and type

```
cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_available_frequencies
```

and 

```
cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_cur_freq
```

Post the results back here by copying and pasting from the terminal.

Kind regards

---

### Post by davesbrain on 2012-05-23
I've been reading it's most likely the cool&quiet.  Pretty unnerving. ](*,)   Wondering if I should 'attempt' a bios upgrade.(to gain some options I don't currently have)
Specs are Biostar K8VGA-M mobo
AMD Athlon 64 3400+
2GB DDR-400

...and the results you asked for:
```
davejr@desktop:~$ cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_available_frequencies
2400000 2200000 2000000 1800000 1000000 
davejr@desktop:~$ cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_cur_freq
1000000
davejr@desktop:~$ 

```

---

### Post by davesbrain on 2012-05-23
JJiggens is right.   Couple webtabs open and a streaming Hulu.  Now reporting as 2400.

```
davejr@desktop:~$ cat /proc/cpuinfo
processor	: 0
vendor_id	: AuthenticAMD
cpu family	: 15
model		: 12
model name	: AMD Athlon(tm) 64 Processor 3400+
stepping	: 0
cpu MHz		: 2400.000
cache size	: 512 KB
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 1
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext lm 3dnowext 3dnow up
bogomips	: 4799.23
clflush size	: 64
cache_alignment	: 64
address sizes	: 40 bits physical, 48 bits virtual
power management: ts fid vid ttp

davejr@desktop:~$ 

```

But thank you guys anyways.

---

### Post by matt_symes on 2012-05-24
Hi

> **davesbrain said:**
> I've been reading it's most likely the cool&quiet.  Pretty unnerving. ](*,)   Wondering if I should 'attempt' a bios upgrade.(to gain some options I don't currently have)
Specs are Biostar K8VGA-M mobo
AMD Athlon 64 3400+
2GB DDR-400

...and the results you asked for:
```
davejr@desktop:~$ cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_available_frequencies
2400000 2200000 2000000 1800000 1000000 
davejr@desktop:~$ cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_cur_freq
1000000
davejr@desktop:~$ 

```

Yep. The frequencies are there. It is just scaling down on the work load you were using at the time when you first checked /proc/cpuinfo.

You can change to the performance governor if you want. That should run at maximum clock speed but at reduced  battery life and is not really worth it.

Take a look  at this

```
matthew@matthew-Aspire-7540 ~/my_storage/linux-3.4.0-3.7
 % cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_governors 
conservative ondemand userspace powersave performance 
matthew@matthew-Aspire-7540 ~/my_storage/linux-3.4.0-3.7
 % cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor 
ondemand
matthew@matthew-Aspire-7540 ~/my_storage/linux-3.4.0-3.7
 % cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_cur_freq
800000
800000
matthew@matthew-Aspire-7540 ~/my_storage/linux-3.4.0-3.7
 % echo performance | sudo tee /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor
[sudo] password for matthew: 
performance
matthew@matthew-Aspire-7540 ~/my_storage/linux-3.4.0-3.7
 % cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_cur_freq                        
2000000
2000000
matthew@matthew-Aspire-7540 ~/my_storage/linux-3.4.0-3.7
 % 

```

You can change the governor you want by editing /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor.

Editing the running governor this will way not persist after reboots though.

As for your BIOS update, be careful. I only update a BIOS when i _really_ need to. I have created some bricks in the past :)

EDIT: You edited your post about the BIOS update ?

Kind regards

---

### Post by davesbrain on 2012-05-25
Thank you for that tip on the governor.  I think I'll leave it alone and just use it as is.   I 'guess' it's a neat feature that would prolong the life of the cpu.

As for the bios, I have NOT updated it and I'm not sure I will.  Yea, I know, it's a biggie.   I was sold a 'brick from hosed bios update' for dirt cheap a long time ago.  I found a guy on Ebay that would send you a new chip, with proper bios for $10 plus your old chip as a core trade.  Worked out pretty good and that Asus A7V was saved. :D

*the edit I inserted was just the Thank You towards you guys for the help.

---

